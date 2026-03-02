**How to Change HC-05 Name to "Ctrlnest"**

🔹 **Step 1:** Put HC-05 in AT Mode Disconnect power.
Hold the EN/KEY button on HC-05.
While holding, power ON the module.
LED should blink slowly (2 sec interval) → AT mode activated.

🔹 **Step 2:** Upload This Temporary AT Code

**Upload this simple sketch to ESP8266:**

#include <SoftwareSerial.h>

SoftwareSerial bt(D4, D8);  // RX, TX

void setup() {
  Serial.begin(9600);
  bt.begin(38400);   // AT mode default baud rate
  Serial.println("Enter AT commands:");
}

void loop() {
  if (Serial.available()) {
    bt.write(Serial.read());
  }
  if (bt.available()) {
    Serial.write(bt.read());
  }
}



🔹 **Step 3:** Send These Commands in Serial Monitor
SET
**Baud: 9600**

**"Both NL & CR"**

**Then type**:

AT

You should get:

OK

Now change name:

**AT+NAME=CtrlNest**

Response:

OKsetname
🔹 Step 4: Power OFF → Power ON Normally

Now when you scan Bluetooth, it will show:

👉 Ctrlnest

✅ **After That**

Upload your original Sinric + Bluetooth code again.
No changes needed in your main program.
