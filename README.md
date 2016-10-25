# Introduction

This is an implementation of a userspace driver for using the Boogie Board Sync
as a tablet under linux.  There are two apps, one for usb input and one for
bluetooth.  It uses pyusb/pybluez to interface with the device and the UInput
system (via evdev for python) to generate input signals.

# Requirements

- python
- pyusb (for usb) (python-usb)
- pybluez (for bluetooth) (python-bluez)
- evdev

Be sure to use the right python version of your system. On Debian it might be required to use pip3 install.

# Usage

For the USB app, plug in the device and run the app.

For bluetooth, it should scan for your device (put it in pairing mode!), so simply running it should work.  If not, run blue.py with a specific address (e.g., ./blue.py 00:00:00:00:00:00) which you can discover using "hcitool scan".

In both cases the boogie board should not be mounted. Otherwise the scripts will not work.

Your need root permissions to run the scripts in python.

You can limit your device to one screen, if you use several displays at once, using xinput. Simply run
xinput
to scan for your devices. Find the id of your boogie-board-sync-pen.
Then use
xinput map-to-output $ID $SCREEN

with $ID as the id of your boogie-board-sync-pen and $SCREEN as the name of the display you want to map it to. Then the boogie board will be maped to the dimensions of the specified screen and you can not move the pointer outside of this screen.

I recommend Xournal on linux as a writting tool.

# Bugs

# Debian / Ubuntu changes
There are differences in the evdev Package between ubuntu and debian! A different syntax in the call of absolute values in evdev is needed! See the differences in the uploaded files.
