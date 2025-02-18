# inkplate-dashboard

PlatformIO project for using the Inkplate 10 E-ink display as a wall-mounted dashboard. A fork of the excellent [lanrat/homeplate](https://github.com/lanrat/homeplate) project, with minor adjustments for using it with [petterhj/homeassistant-dashboard-server](https://github.com/petterhj/homeassistant-dashboard-server). See the [original documentation](https://github.com/lanrat/homeplate#readme) for more details.

## Usage

Install [PlatformIO](https://platformio.org/). Then copy `src/config_example.h` to `src/config.h` and enter your settings.

Build & run with:

```shell
pio run
```

The first flash/installation needs to be done over USB. Future updates can be done over USB or WiFi with:

```shell
pio run -e ota
```

To monitor serial output without re-flashing:

```shell
pio device monitor
```

### Updating

```shell
git pull
pio upgrade
pio pkg update
pio run --target clean
```

### WSL

Using PlatformIO under WSL on Windows is not really straightforward. This is a workaround, while somewhat cumbersome, to be able to continue developing under WSL (given that PlatformIO is installed on the host system):

```sh
$ rsync -avv . /mnt/c/Users/<username>/src/inkplate-dashboard \
    --exclude .pio \
    --exclude .git
```

```sh
cd C:\Users\<username>\src\inkplate-dashboard
C:\Users\<username>\.platformio\penv\Scripts\activate
pio pkg update
pio run -e inkplate10 --upload-port COM3 --monitor-port COM3
```
