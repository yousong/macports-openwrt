**This is currently NOT maintained in favor of https://github.com/yousong/build-scripts**

This is Portfile repository mainly for porting packages such as libubox, ustream-ssl, etc. from OpenWrt project to Mac OS X.  Also included are some utilities not included in upstream MacPorts yet, e.g. halibut, tweak, etc.

## How to use it.

1. MacPorts has to be installed.  `/opt/local` as the installation prefix path will be assumed in the following text.
2. Clone this repository to local machine.
3. Edit `/opt/local/etc/macports/sources.conf` to add a path to the repository, such as the following.

		file:///Users/yousong/dev/macports-openwrt

	Most of the time, you will just need to append a line as above, leaving what's already there untouched.

4. Use it.

	- Generate port index.

			cd /Users/yousong/dev/macports-openwrt
			portindex

	- Search for packages in it to see if it has been indexed.

			port search libubox

	- Bulid and install them.

			sudo port build libubox
			sudo port install libubox


## Tips

Sometimes I found it useful to have handy shell function ready when testing the build.

	function reinstall() {
		local name="$1"
		sudo port uninstall "$name"
		sudo port clean "$name"
		sudo port install "$name"
	}

Build logs can be found at the following places if anything wrong happened.  The actual path can vary, be sure to read the output from the port command.

	/opt/local/var/macports/build/_Users_yousong_dev_macports-openwrt_devel_libubox/libubox/work/libubox-20150115/CMakeFiles/CMakeError.log
	/opt/local/var/macports/build/_Users_yousong_dev_macports-openwrt_devel_libubox/libubox/work/libubox-20150115/CMakeFiles/CMakeOutput.log
