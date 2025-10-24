Portable Smart & High-Fidelity Audio System

🎯 Overview

This project details the design and construction of a high-fidelity portable audio system built from the ground up. Unlike off-the-shelf speakers, this system is a "smart" device centered around an ESP32 microcontroller. It manages a multi-source audio input (Bluetooth, AUX, Mic), digital volume control, and status updates on an OLED display.

The core audio path is built for audiophile performance, using a PCM5102A DAC for digital signals and a TPA3116D2 Class-D amplifier for powerful, efficient sound. The entire system is housed on a custom-designed motherboard with a complex, isolated power system, a dedicated mobile app for EQ control, and built-in power bank functionality.

✨ Key Features

🔊 High-Power 60W Stereo Output: Driven by a TPA3116D2 Class-D amplifier for loud, clear, and efficient audio reproduction.

🧠 Smart Core (ESP32): Manages all system logic, Bluetooth (A2DP), digital volume, and the user interface.

📱 Mobile App Integration: A dedicated mobile app allows for remote control of volume and fine-tuning of Treble and Bass through a software equalizer.

🎛️ Multi-Source Audio Input: A CD4052 MUX seamlessly switches between high-fidelity Bluetooth (processed by the DAC), a 3.5mm AUX jack, and an external microphone input.

💡 OLED Status Display: A crisp OLED screen, controlled by a rotary encoder, provides real-time information on the current audio mode (Bluetooth/AUX/Mic) and volume level.

🔋 Extended 10+ Hour Battery Life: Powered by a custom 3S2P (11.1V) Li-ion battery pack with a dedicated Battery Management System (BMS) for safe and reliable operation.

⚡ Dual-Port Power Bank: Integrated USB-A ports allow the speaker to function as a high-capacity power bank, charging two mobile devices simultaneously.

🔌 Custom PCB & Isolated Power: A custom 2-layer motherboard was designed in Eagle, featuring separate boost and buck converters to create isolated power rails (24V for Amp, 5V for USB, 3.3V for logic) to eliminate noise.

🛠️ Tech Stack & Key Components

Microcontroller: ESP32 (30-pin)

DAC (Digital-to-Analog): PCM5102A

Amplifier: TPA3116D2 (A543) Class-D Amplifier

Audio Switch: CD4052 Analog Multiplexer (MUX)

Power System: 3S2P (11.1V) Li-ion Pack + 3S BMS

Power Converters: 1x Boost (24V), 2x Buck (5V, 3.3V)

User Interface: 0.96" OLED Display & Rotary Encoder

Software: Arduino IDE (C++)

Libraries: AudioTools, BluetoothA2DPSink

PCB Design: Autodesk EAGLE

🔧 Design & Engineering Process

1. System Architecture

The system is an ESP32-centric design. The ESP32 acts as the "brain," handling Bluetooth audio, UI logic (OLED/Encoder), and digital EQ. It commands the CD4052 MUX to select the audio source.

2. Audio Signal Path

Two distinct paths are fed into the MUX:

Digital Path: Bluetooth -> ESP32 (for processing/EQ) -> I2S -> PCM5102A DAC -> MUX

Analog Path: AUX/Mic Jack -> MUX

The selected source from the MUX is then passed to the TPA3116D2 amplifier and finally to the speakers.

3. Power System Design

To prevent noise and ensure stability, three separate DC-DC converters are used, all fed from the 3S battery:

Boost Converter (24V): Provides a high-voltage rail exclusively for the TPA3116D2 amplifier to achieve maximum power.

Buck Converter (5V): Provides a clean 5V rail for the USB power bank ports and 5V logic.

Buck Converter (3.3V): Provides a dedicated, noise-free 3.3V rail for the sensitive ESP32 and DAC.

4. Software & Logic

The firmware, developed in the Arduino IDE, uses a state machine to manage the user's mode selection from the rotary encoder (BT/AUX/Mic). The AudioTools and BluetoothA2DPSink libraries handle the complex audio pipeline, allowing for digital processing of the Bluetooth stream before it is sent to the DAC.

📈 Performance Results

Power Output: 2x 50W into 4Ω at 21V (derated to ~2x 15W at 11.1V battery)

Total Harmonic Distortion (THD+N): < 0.1% @ 1W (Measured)

Frequency Response: 50Hz – 20kHz (± 3dB)

Battery Life: 10+ hours of continuous playback.

💰 Cost & Market Comparison

A key goal of this project was to demonstrate that a high-performance audio system could be built locally at a fraction of the cost of imported commercial equivalents.

Total Build Cost: The entire system was built with a component cost of approximately ৳5,000 BDT.

Market Value: A comparable "smart" speaker from an international brand (with similar features like a DAC, Class-D amp, 60W output, and smart controls) would retail in the Bangladeshi market for over ৳15,000 BDT.

This project proves the viability of designing and building complex, cost-effective consumer electronics locally.

🚀 Future Work

Finalizing the software for the mobile app's Treble and Bass controls. ( It was not integrated with Project, just to show an DEMO, how it looks and how it will work) 

Designing and 3D printing a custom, acoustically-optimized enclosure. (Only designed the All GND connection part, due to unavailability of local 2 layer pcb printing and shorter time span) 

Implementing functional USB Type-C PD (Power Delivery) charging.

Processing the analog AUX input using the ESP32's DSP capabilities.

📸 Photos & Schematics

Hand Drawn Diagram attached. 
Final Build in group photo
Custom PCB Design (Eagle):
System Block Diagram:
