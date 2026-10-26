# BMS Basics

## What is a BMS?

A Battery Management System (BMS) monitors and protects a rechargeable battery pack. It helps the battery operate safely and reliably during charging and discharging.

## Four Core Functions

1. Monitoring: Measures cell voltage, pack current, and temperature.
2. Protection: Detects overvoltage, undervoltage, overcurrent, short circuit, and overheating.
3. Control: Controls charge and discharge MOSFETs and performs cell balancing.
4. Communication: Sends battery status and fault information to other devices.

## Important Distinction

A BMS is usually not a battery charger. The charger supplies electrical energy, while the BMS monitors the battery and decides whether charging or discharging is safe.## Main Hardware Blocks

| Hardware Block | Example in BMS C1 | Simple Function | Supply Chain Importance |
|---|---|---|---|
| Battery monitor / AFE | Texas Instruments BQ76952 | Measures cell voltage, current, and temperature and provides protection functions | Critical IC; difficult to replace directly |
| Microcontroller / MCU | Espressif ESP32-C3 | Runs control logic and manages communication | Critical programmable IC |
| Power MOSFET | N-channel MOSFETs | Opens or closes the high-current charge and discharge path | Important for current capacity and heat generation |
| Current shunt | Low-resistance shunt | Converts battery current into a small measurable voltage | Accuracy and power rating are important |
| Balancing circuit | Resistors and switching components | Discharges higher-voltage cells slightly to reduce cell imbalance | Affects battery consistency |
| Temperature sensor | NTC thermistor | Detects battery, MOSFET, and board temperature | Important safety component |
| Passive components | Resistors and capacitors | Filtering, voltage division, timing, and circuit stability | Many alternatives, but specifications must match |
| Connectors | Signal and power connectors | Connects cells, sensors, communication, and external equipment | Mechanical compatibility is important |
| Communication interface | CAN, RS-485, USB, UART, I2C | Transfers battery status and fault information | Interface chips may create supply risk |

## Simplified Hardware Logic

1. Sensors measure cell voltage, current, and temperature.
2. The BQ76952 processes measurements and detects unsafe conditions.
3. The ESP32-C3 runs system logic and communicates with external devices.
4. MOSFETs control whether charging and discharging are allowed.
5. Connectors and communication circuits link the BMS with the battery pack, charger, inverter, or computer.