# Imgoverlay

Vulkan/OpenGL overlay renderer (shared memory or texture).  
Included QtWebEngine client allows to use any web page as overlay.

Started as [MangoHud](https://github.com/flightlessmango/MangoHud) fork.

## Building

#### Dependencies
* glslangValidator
* python3
* Xlib
* Qt5 - Core, Network, Widgets, WebEngineWidgets, QuickWidgets
* EGL

#### Build
```sh
meson build
meson install
```
ArchLinux: [PKGBUILD](dist/PKGBUILD)

# Usage

## Run Vulkan/OpenGL app
```sh
# Vulkan
IMGOVERLAY=1 /path/to/app
# OpenGL
imgoverlay /path/to/app
```

#### Configuration (app)
* `IMGOVERLAY_CONFIGFILE` env variable
* `~/.config/imgoverlay/<APP>.conf` (eg. `~/.config/imgoverlay/vkcube.conf`)
* `~/.config/imgoverlay/imgoverlay.conf`

```ini
socket=/tmp/imgoverlay.socket
toggle_overlay=Shift_R+F12
```

## Run client
```sh
imgoverlayclient [--tray] [config-file]
```
* `--tray` start minimized in system tray
* `--shm` use shared memory instead of DMA-BUF (required for GLX currently)
* `--disable-gpu` disable QtWebEngine GPU rendering
* `config-file` path to config file (default `~/.config/imgoverlayclient.conf`)

#### Configuration (client)

```ini
[General]
Socket=/tmp/imgoverlay.socket
Cache=cache

[Github_example]
Url=https://github.com/nowrep/imgoverlay
X=0
Y=0
Width=200
Height=200
InjectScript=script.js

[Another_site]
Url=https://google.com
X=210
Y=210
Width=100
Height=100
```
