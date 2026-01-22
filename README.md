# Esp32-Bluetooth-Serial

<p align="center">
    <img src="IdkWhatIMake.png" width=300>
</P>

Controlling the ESP32 microcontroller in Bluetooth serial using voice commands on an Android-based mobile phone from vosk.android.demo by calling the ESP32 function with the variables it has. 

For example :
```c
#include "BluetoothSerial.h"

BluetoothSerial SerialBT;

const int relayPin = 16;
const int oePin    = 22;

void setup() {
  pinMode(oePin, OUTPUT);
  digitalWrite(oePin, HIGH);      // OE aktif

  pinMode(relayPin, OUTPUT);
  digitalWrite(relayPin, HIGH);   // relay OFF (active LOW)

  Serial.begin(115200);
  SerialBT.begin("ESP32-Roboboy");
}

void loop() {
  if (!SerialBT.available()) return;

  char cmd = SerialBT.read();

  // filter input valid
  if (cmd != 'A' && cmd != 'a') return;

  if (cmd == 'A') {
    digitalWrite(relayPin, LOW);    // relay ON
  }
  else if (cmd == 'a') {
    digitalWrite(relayPin, HIGH);   // relay OFF
  }
}

So in Esp Btl you should make :

any command + serial command you like, for example :
command     : turn on relay
serial in   : A

so based on code example above, if you say "turn on relay" it will send serial command A to esp trough bluetooth (you have to connect it first)

and tho you can delete or add your command infinitly

if you want this project you can ask me , even tho ill give you or not based on my mood :)

the screenshot of the app:
![preview](ScrenShot/1000212913.jpg)
![preview](ScrenShot/1000212914.jpg)

