📡 Radar Scanner – Scan Area and Show Distance on Screen
A low-cost radar scanning system built with an Arduino UNO, an HC-SR04 ultrasonic sensor, and an SG90 servo motor, developed as part of the CSE-214 Digital Logic Design Lab at Feni University.
The system sweeps a 180° field of view, measures distance to nearby objects using ultrasonic echolocation, and visualizes the sweep in real time on a Processing IDE-based radar display (plus optional LCD/serial output).

How It Works:
The HC-SR04 sends a 10 µs trigger pulse, emits an ultrasonic burst, and measures the echo return time.
Distance is calculated as:
Distance (cm) = (Time × 0.0343) / 2
The SG90 servo sweeps the sensor from 15° to 165° and back, pausing briefly at each step to let readings stabilize.
Angle + distance pairs are streamed over serial to a Processing sketch, which renders a live radar-style sweep with a highlighted "ping" for detected objects. Components:
Model
Qty
Purpose
Microcontroller
Arduino UNO-1
Main control & logic
Ultrasonic Sensor
HC-SR04-1
Distance measurement
Servo Motor
SG90-1
180° sweep
Jumper Wires
M-M, M-F~10
Circuit routing
Power Supply
5V USB Cable-1
Power + serial data.

Pin Configuration:
HC-SR04
VCC → 5V
TRIG → D10
ECHO → D11
GND → GND
SG90 Servo
Signal (Yellow) → D12
VCC (Red) → 5V
GND (Black) → GND

Repository Structure:
├── arduino/
│   └── radar_scanner.ino      
 Arduino firmware
├── processing/
│   └── radar_display.pde      Processing visualization sketch
└── README.md

Getting Started:
Wire the circuit according to the pin configuration above.
Upload radar_scanner.ino to the Arduino UNO via the Arduino IDE.
Open radar_display.pde in Processing, update the serial port (COM4 by default) to match your system, and run it.
Watch the live radar sweep and object detection on screen.

Results:
The prototype achieved ~95% measurement accuracy against known reference distances across the 0°–180° sweep, with minor deviations attributed to ambient temperature effects, specular reflection on angled surfaces, and mechanical backlash in the servo.

Future Enhancements:

Add Wi-Fi (ESP8266/ESP32) to log detections to the cloud (e.g., Blynk)
Fuse ultrasonic + infrared sensing for material classification
Build a dedicated GUI beyond the Processing sketch.

Reference:
Base project adapted from RoboZenBD's Arduino Beginner to Advanced Learning Kit.
