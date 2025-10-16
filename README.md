SHRIRAM.S(212222020027)
# Anti-Theft-Alert-System-using-Tilt-Sensor

## Aim:
~~~
To measure the tilt Sensor using SW200D with Arduino UNO Board/ESP-32 using Tinker CAD.
~~~
## Hardware / Software Tools required:
	PC/ Laptop with Internet connection
  Tinker CAD tool (Online)
	Arduino UNO Board/ESP-32
	Tilt sensor(SW200D)

## Circuit Diagram:
~~~
<img width="1470" height="738" alt="image" src="https://github.com/user-attachments/assets/e9d198ba-ca8d-4099-90ac-fad1f91791cd" />
~~~
 
## Theory :
 The Arduino Uno is powered by the ATmega328P, an 8-bit microcontroller that runs at 16 MHz. It has 32 KB of flash memory, 2 KB of SRAM, and 1 KB of EEPROM. The board has 14 digital I/O pins (of which 6 can be used as PWM outputs) and 6 analog input pins. These pins allow the board to interface with various sensors, actuators, and other devices.The Arduino Uno can be powered via a USB connection or an external power supply. The board has a built-in voltage regulator to manage power from 7 to 12 volts.
The board is programmable using the Arduino IDE (Integrated Development Environment), which supports a simplified version of C/C++. The code, known as a "sketch," is uploaded to the board via a USB connection. The Uno has a USB-B port, which is used for communication with a computer. The USB connection also powers the board when connected. The board includes a reset button that restarts the microcontroller, useful during programming and troubleshooting. The In-Circuit Serial Programming (ICSP) header allows for low-level programming of the microcontroller or firmware updates. The Uno has a built-in LED on pin 13, commonly used for simple tests and debugging.


## Procedure:

Step 1: Set Up the Tinkercad Environment
•	Log in to Tinkercad: Open Tinkercad in your web browser and log in to your account.
•	Create a New Circuit: In the Tinkercad dashboard, click on "Circuits" and then select "Create New Circuit."
Step 2: Add Components to the Circuit
•	Arduino Uno: Drag an Arduino Uno board from the components panel onto the workspace.
•	SW200D Sensor: Search for the SW200D sensor in the components panel and drag it into the workspace.
•	Breadboard: Drag a small breadboard to the workspace to help with wiring connections.
•	Resistor (Optional): A resistor may not be necessary for this simple setup, but you can include it for more accurate readings.
•	Wires: Use wires to connect the components.

Step 3: Connect the Tilt Sensor (SW-200D) to Arduino:
•	SW200D Vout (Middle Pin) to Arduino Digital Pin (e.g., D2): Use a wire to connect the middle pin (Vout) of the tilt sensor to a digital input pin on the Arduino.
•	SW200D GND (One Side Pin) to Breadboard GND Rail: Connect one side pin of the tilt sensor to the ground rail of the breadboard.
•	SW200D VCC (Other Side Pin) to Breadboard 5V Rail: Connect the other side pin of the tilt sensor to the 5V rail of the breadboard.
Step 4: Write the Arduino Code
•	Code Editor: Click on the "Code" button at the top of the Tinkercad workspace to open the code editor.
•	Set the Coding Mode: Ensure the editor is in "Text" mode to write your code in C/C++.
•	Enter the Code: Write the following code from the SW200D sensor:
Step 5: Simulate the Circuit
•	Start Simulation: Click the "Start Simulation" button at the top of the workspace to run the circuit and code.
•	Monitor Output: Open the serial monitor by clicking the "Serial Monitor" button 
Step 6: Troubleshoot and Refine
•	Check Connections: Ensure that all connections are made correctly on the breadboard and the Arduino.
•	Adjust Code: If needed, tweak the code to improve accuracy or change the format of the output.
Step 7: Save Your Work
•	Stop Simulation: Click "Stop Simulation" to end the simulation.
•	Save the Circuit: Click "Save" to keep your circuit design and code for future use.

## Code:
~~~
#include <LiquidCrystal.h>

LiquidCrystal lcd(12, 11, 5, 4, 3, 2);
int motionDetect = 7;
int secs = 0;

void setup() {
  Serial.begin(9600);
  lcd.begin(16, 2);
  pinMode(6,OUTPUT);
  pinMode(motionDetect,INPUT);
  pinMode(A0, OUTPUT);
 
}

void loop() {
  int detect = digitalRead(motionDetect);
  lcd.setCursor(0,0);
  if (detect==1){
    detected();
  }
  else{
    lcd.print("No Motion");
    lcd.setCursor(0,1);
    lcd.println("Detected!");
    digitalWrite(6, LOW);
    delay(500);
    secs = 0;
    
  }
  
  
}

void detected(){
  
  lcd.print("Motion Detected!");
  secs++;
  Serial.println(secs);
  digitalWrite(6, HIGH);
  warning(secs);
  delay(1000);
  lcd.clear();
}

void warning(int num){
  if (num == 3){
    for(int i=0; i<num; i++){
      tone(A0, 880, 100);
      delay(100);
    }
  }
  else if (num == 6){
    for(int i=0; i<num; i++){
      tone(A0, 988, 250);
      delay(100);
     
    }
  }
  else if (num == 8){
    for(int i=0; i<num; i++){
      tone(A0, 1047, 500);
      delay(100);
    }
    secs = 6;
  }
  
}
~~~
## Output:
~~~
 https://go.screenpal.com/watch/cT6DDwnbUHF
~~~

## Result:
~~~
Thus the Anti-Theft-Alert-System-using-Tilt-Sensor is performed.
~~~


Result: Thus measure the Tilt Sensor using SW200D with Arduino UNO Board/ESP-32 using Tinker CAD has been Verified Successfully.

