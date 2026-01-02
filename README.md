# Samsung FRP Bypass

Unlock the Google Account Factory Reset Protection on Samsung devices.

Adjusted for new Samsung firmware update - also working with 2022-2024 software. No need to run suspicious closed-source Windows tools!

This fork fixes small bugs from previous fork (schorschii/Samsung-FRP-Bypass) and extends this documentation

## How to use

- Before running the python script, make sure your system meets all the requirements (optionally replace `apt` by `dnf` if running on a RHEL/Fedora based system):
  - Ensure that the pip tool is available `sudo apt install pip`
  - Install the required python dependencies via pip `pip install -r requirements.txt`
  - Make sure you have the Android Debug Bridge (adb) installed `sudo apt install adb`

- On your Samsung device, perform a hard factory reset using the volume and power button (see: https://www.androidauthority.com/factory-reset-android-1119937/#4)

- After the boot has finished, **don't** connect to any wi-fi and **don't** follow the setup of the device

- Just tap on the emergency call button in the bottom corner and dial `*#0*#` to open the factory tests page

- Connect the phone via usb and run `python main.py`

- When asked, enter the so called serial port (=device id) of the connected Samsung phone or, if matching already, accept the proposed default. It looks like `/dev/ttyXXX` and the correct one should show something similar to the string "SAMSUNG_Android - CDC Abstract Control Model (ACM)" next to the serial port

- Wait for the success message.
  - Do not panic if an exception is thrown. Two commands ("com.google.android.gsf.login/" and "com.google.android.gsf.login.LoginActivity") seems to fail on some devices. According to @schorschii these are additional unlock commands that may be necessary for specific models.
  - The device should start up automatically into the home screen of an almost virgin Android OS.
  - **Don't stop here**, even if the problem seems to be solved yet! You must perform the next step as well ...

- Now trigger a "normal" factory reset using the settings app (see: https://www.androidauthority.com/factory-reset-android-1119937/#3)

- After the factory reset has completed, you are done and the FRP should be unlocked from your device :iphone::tada:

- From now on you can follow the setup of the phone as usual and link it with any Google account :beers:
