# Fluidd
Fluidd is a free and open-source Klipper web interface for managing your 3d printer.

<img src="https://raw.githubusercontent.com/cadriel/fluidd/develop/.github/images/Printing.png">

## Coming Soon
- [ ] Flesh out installation instructions / automation
- [ ] Replace favicon
- [ ] Add temperature presets
- [ ] Add bed levelling
- [ ] Filament sensor check
- [ ] Endstops check
- [ ] Add light theme
- [ ] Add gcode metadata
- [ ] Allow moving files / folders
- [ ] Configuration file lists / editing

## Getting Started
Follow the steps below:

### ⏳ Installation

A completed installation should have a folder structure similar to the following;

```
~ /
  /gcode_files
  /moonraker
  /moonraker-env
  /fluidd
  /klipper
  /klippy-env
  /klipper_config
    printer.cfg
    moonraker.conf
  /gcode_files
```
---

#### Operating System
---
Fluidd and its dependenceis are best installed on a [fresh Raspbian](https://downloads.raspberrypi.org/raspios_lite_armhf_latest) (or similar) image. Please
**do not** install on top of an Octopi image, as this *will* cause issues.

You can download raspbian [here](https://downloads.raspberrypi.org/raspios_lite_armhf_latest).

Continue once you have a bootable image that you can ssh into.

---
#### Klipper
---
Next, you should focus on a working klipper installation.

A good start would be klippers own installation instructions found here:
https://www.klipper3d.org/Installation.html

However, please ensure you avoid installation on Octopi.

Once you've completed this, you should have the `klipper` and `klippy-env` folders in place. 

---
#### Moonraker
---
Moonraker is the API that exposes Klipper to clients such as Fluidd.

Moonraker is best installed by following its installation documentation found [here](https://github.com/Arksine/moonraker/blob/master/docs/installation.md).

After its installation, you'll want to update the klipper configuration to the following;
```
# Configuration for /etc/init.d/klipper

KLIPPY_USER=pi

KLIPPY_EXEC=/home/pi/klippy-env/bin/python

KLIPPY_ARGS="/home/pi/klipper/klippy/klippy.py /home/pi/klipper_config/printer.cfg -l /tmp/klippy.log -a /tmp/klippy_uds"
```
This ensures the `printer.cfg` is where moonraker, klipper and fluidd will expect it.

---
#### Fluidd
---

Now is a good time to ensure you have the `sdcard` and `klipper_config` folders created. Also ensure your `printer.cfg` has been copied to the `klipper_config` folder. 

Please also ensure your printer.cfg has the following lines;

```
[pause_resume]

[display_status]

[virtual_sdcard]
path: ~/gcode_files
```

... more to come ...