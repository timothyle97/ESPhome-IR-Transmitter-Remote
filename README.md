# ESPhome-IR-Transmitter-Remote
Yaml code example for an IR transmitter in ESPhome.

IR-Transmitter.yaml: Modified for use with NEC devices. WiFi parameters moved to secrets file. 
Used NEC conversion from https://gist.github.com/kelvie/891fc8bfc8353594136ee1ac790e60f7

IR-Transmitter-Astra-Samsung.yaml: Modified for an Astra AR4GBAL Smart Home Module controlling an IR blaster and relay module. 
Used Samsung IR Code conversion listed below. 
Example of the Smart Home Module playing music with the buzzer: https://youtu.be/OEd-MD4axUU


# Usage
- Change the SSID and password to that of your network, or point them to a secrets file. Also don't forget to set your IP network settings or simply copy/paste in your known good esphome wifi code block which you use with your other sensors/nodes.
- Depending on your set-up you will need to change the board variable to your corrosponding board model.
- Also don't forget to change pin assignments and variable names, as this IR transmitter example is from my bedroom.

# Getting Your Remote Codes
- This code example uses NEC codes, other codes can be found online by searching 'tv brand' IR codes.
- If you're unable to find codes, the codes you find do not work for your TV, or ou have an off brand Aldi TV brand like Bauhn, etc. you can acquire your codes by using the IR sensor.yaml.
- This latest commit has the codes switched to Samsung codes. The samsung_tv_remote_codes details the code conversions specifically frome ESPHome. They were calculated using this guide (and quoted below): https://stackoverflow.com/questions/60718588/understanding-ir-codes-for-samsung-tv
  - Bit-reverse the device number '07' to get 'E0'
  - Bit-reverse the subdevice number (also '07') to get 'E0'
  - Convert 152 to hexadecimal and reverse the bits to get '19'
  - Calculate the last two digits as ( 0xFF - the bit-reversed OBC ), 0xFF - 0x19 = 0xE6, giving the final 8 bits 'E6' (example hex calculator: https://www.calculator.net/hex-calculator.html)
- The full list of Samsung remote codes can be found here: https://github.com/probonopd/irdb/blob/master/codes/Samsung/TV/7%2C7.csv

# IR Sensor.
- This yaml code allows you to view all captured codes within an ESPhome terminal either over serial or OTA.
- Note down these codes for every function and copy them across to the corrosponding template switches.
 I recommend you do a few presses for each button function to see if the sensor outputs a JVC or LG tv code value, as these can be easier to use and more accurate to replay than raw codes.

Feel free to use this code however you please.


