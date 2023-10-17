# LED Blinker F´ Project

<img src="https://user-images.githubusercontent.com/30123691/186647333-c7c3bd66-bbe6-4111-aabb-e03b9893b243.png" alt="f-prime logo" width="1000"/>

F´ (F Prime) is a robust, component-driven framework developed by NASA that empowers developers to rapidly create and deploy spaceflight and embedded software applications. For detailed information about F´, you can visit the official [F´ website](https://nasa.github.io/fprime/).

## Project Overview

This LED Blinker F´ Project is an exercise in utilizing NASA's F´ framework to create a fully functional spaceflight software component and run it on physical embedded hardware.

The primary objective of this project is to create a spaceflight component that can execute commands and respond to events in a manner consistent with the operation of a satellite. This component is then loaded onto an ARM processor, simulating the real-world interaction between a ground-station program and physical embedded hardware.

## Key Project Elements
This project encapsulates several crucial aspects of NASA's principles for effective flight software development:

* **Software Requirements and Architecture:** The project delves into NASA's standard software requirements and planning architecture process. It emphasizes the importance of well-defined software specifications and requirements such that ownership of different modules of the software can be properly communicated and delegated between design team and the software team implementing said design.

* **Timing and Prioritization:** Timing is critical in spaceflight software. This project underscores the significance of properly prioritizing the execution of critical components over non-critical components to ensure the system's reliability.

* **Error Handling:** Safe and effective error handling is an integral part of any spaceflight software. This project offers insights into handling critical errors in a manner that ensures the spacecraft is in an entirely safe state before critical errors are addressed or systems rebooted altogether.

* **Command, Event, and Telemetry Communication:** It also explores the use of commands, events, and telemetry to facilitate seamless communication between the ground station and embedded hardware.

## Getting Started

To run this project and simulate the communication between the groundstation and the satellite, you'll need to follow these steps:

### Building the Project

Before you can start using the project, you'll need to build it. Open your terminal and navigate to the project directory, its components, and the deployment:

```bash
cd fprime-led-blinker # Top project directory
fprime-util build
cd fprime-led-blinker/Components # Components folder
fprime-util build
cd fprime-led-blinker/LedBlinker # Deployment folder
fprime-util build -j4
```

### Starting the Deployment

To start the ground station deployment, run the following command in the LedBlinker folder:

```bash
fprime-gds  --ip-client
```

This command will launch the F´ Ground Data System (GDS), and the F´ GDS control page should automatically open in your web browser. If the web page doesn't open automatically, you can access it by navigating to http://127.0.0.1:5000 in your web browser.

## Interacting with the Web Browser Client

Once the F´ GDS control page is open in your web browser, you can interact with the groundstation and send communication commands to the simulated satellite. Here is a simple test you can run:

1. **Send a Command:** select the ‘Commanding’ tab, search for led.BLINKING_ON_OFF and send it with the argument set to ON.
1. **Verify Event:** select the ‘Events’ tab and verify that the SetBlinkingState event reports the blinking state was set to ON.
