# EXPERIMENT-03-INTERFACING-DIGITAL-SENSOR-WITH-EDGE-DEVELOPMENT-BOARD-
 
### NAME: YOGESH RAO S D
### ROLL NO: 212222110055
### DATE OF EXPERIMENT: 

## **AIM:**  
To interface a **DHT22 temperature and humidity sensor** with the **Raspberry Pi Pico** and display the sensor readings using MicroPython.

## **APPARATUS REQUIRED:**  
1. Raspberry Pi Pico  
2. DHT22 Temperature & Humidity Sensor  
3. 10kΩ Pull-up Resistor (if required)  
4. Jumper Wires  
5. Breadboard  
6. USB Cable  
7. Computer with Thonny IDE  

## **THEORY:**  
### **About Raspberry Pi Pico:**  
Raspberry Pi Pico is a microcontroller board based on the **RP2040 chip**. It features:  
- Dual-core ARM Cortex-M0+ processor  
- 26 multi-function GPIO pins  
- Supports **MicroPython** and **C/C++**  
- Interfaces like **I2C, SPI, UART, and PWM**  
- Low power consumption, ideal for **IoT applications**  

### **About DHT22 Sensor:**  
The **DHT22** is a **temperature and humidity sensor** with a digital output. It has:  
- Operating Voltage: **3.3V – 5V**  
- Temperature Range: **-40°C to 80°C (±0.5°C accuracy)**  
- Humidity Range: **0% – 100% (±2-5% accuracy)**  
- **Data format**: Uses **single-wire communication protocol**  

The sensor measures **temperature using a thermistor** and **humidity using a capacitive sensor**. The **MicroPython dht library** processes the raw data.

## **WORKING PRINCIPLE:**  
1. The **DHT22 sensor** is connected to the **Raspberry Pi Pico**.  
2. The **Pico reads temperature and humidity values** from the sensor via a single-wire communication protocol.  
3. The data is **processed and displayed on the serial monitor**.  
4. If **temperature or humidity crosses a threshold**, an LED can **flash as an alert**.  

## **CIRCUIT DIAGRAM:**  
### **Connections:**  

| DHT22 Pin | Raspberry Pi Pico Pin |
|-----------|----------------------|
| VCC (Pin 1) | 3.3V or 5V |
| Data (Pin 2) | GP15 |
| GND (Pin 4) | GND |
| **(Optional: 10kΩ pull-up resistor between VCC & Data pin)** | |

## **PROGRAM (MicroPython)**  
``` 
import machine
import dht
import time

dht_pin = machine.Pin(0)
dht_sensor = dht.DHT22(dht_pin)

while True:
    try:
        dht_sensor.measure()
        temperature_celsius = dht_sensor.temperature()
        humidity_percent = dht_sensor.humidity()

        print("Temperature: {:.2f} °C".format(temperature_celsius))
        print("Humidity: {:.2f} %".format(humidity_percent))

    except Exception as e:
        print("Error reading DHT:", str(e))

    time.sleep(1)
```

## **OUTPUT:**  
 <img width="1920" height="1080" alt="Screenshot 2025-09-06 161841" src="https://github.com/user-attachments/assets/b28d65a3-3eab-42c4-b26f-9bcb3f743d51" />

## **RESULT:**  
The **DHT22 sensor** was successfully interfaced with the **Raspberry Pi Pico**, and real-time **temperature and humidity data** were read and displayed. The LEDs responded correctly when the threshold limits were exceeded.


 
