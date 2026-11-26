# xptsp OpenWrt Feed

An OpenWrt package feed containing additional command-line packages, LuCI applications and themes, kernel modules, and related utilities. Some components are maintained in this repository; others are included as Git submodules and retain their own upstream documentation and licensing.

## Add the feed

From an OpenWrt source tree, add this line to `feeds.conf.default` (or `feeds.conf`):

```text
src-git xptsp https://github.com/xptsp/openwrt-feed.git
```

Then fetch the feed and install the packages you want:

```sh
./scripts/feeds update xptsp
./scripts/feeds install -a -p xptsp
```

Configure the selected packages in the OpenWrt build system:

```sh
make menuconfig
```

Packages from this feed appear in their usual OpenWrt categories. Select them, save the configuration, and build OpenWrt as usual. Package availability depends on the target, architecture, and OpenWrt version.

## Contents

| Directory | Contents |
| --- | --- |
| `packages/` | Utilities and services including `bcrypt-tool`, `chroot-mount`, `e2guardian`, `media-downloader`, `mwgp`, `peanut`, `port-trigger`, `privoxy-blocklist`, `reddragon-webservices`, `saned-initd`, `twin-bcrypt-js`, `vlmcsd`, and `ympd`. |
| `luci/` | LuCI applications for AdGuard Home, Alpha and Argon configuration, fan control, nginx management, NoDogSplash, Squid, ympd, and listening ports; plus the Alpha, Argon, Aurora, Footstrap, Proton 2025, and shadcn themes. |
| `kmods/` | The `rtl88x2bu-cl` wireless driver and Ugreen-related kernel modules and HDD LED monitoring packages. |
| `fancontrol/` | Fan-control packages and their companion LuCI application. |
| `clevis/` | Clevis, luksmeta, and a LuCI interface for Clevis. |
| `tpm2/` | TPM 2.0 tools, libraries, and related packages. |

For package-specific configuration, dependencies, and usage, see the README in the relevant package directory. Submodules may also link to their upstream project for the latest documentation.

## Clone for development

To work on the feed locally, clone it with its submodules:

```sh
git clone --recurse-submodules https://github.com/xptsp/openwrt-feed.git
```

If you already cloned without submodules, initialize them with:

```sh
git submodule update --init --recursive
```

OpenWrt feed packages are described by their package `Makefile`s. Changes to a submodule are managed in that component's own repository, while this feed records the selected submodule revision.
