# Adaptive Cruise Control System Using MATLAB and Simulink

![MATLAB](https://img.shields.io/badge/MATLAB-R2026a-orange)
![Simulink](https://img.shields.io/badge/Simulink-26.1-blue)
![Control System](https://img.shields.io/badge/Control%20System-PI%20Controller-green)
![Automotive](https://img.shields.io/badge/Domain-Automotive-red)

## 📌 Project Overview

This project presents the modeling and simulation of an **Adaptive Cruise Control (ACC) system using MATLAB and Simulink**.

The system adjusts the ego vehicle's target speed according to the speed and distance of a lead vehicle. When the lead vehicle slows down, the ACC system reduces the ego vehicle's target speed and maintains a desired following distance.

The project demonstrates the complete implementation of an Adaptive Cruise Control system using MATLAB numerical simulation and Simulink.

## 🎯 Project Objective

The main objective of this project is:

> To design, simulate, and analyze an Adaptive Cruise Control system using MATLAB and Simulink that adjusts the ego vehicle's speed according to the lead vehicle while maintaining a desired safe following distance.

## 🛠️ Technologies Used

- MATLAB R2026a
- Simulink 26.1
- MATLAB Function Block
- PI Controller
- Discrete-Time Integrator
- Gain Blocks
- Saturation Block
- From Workspace Block
- Simulink Scopes
- Numerical Simulation

## 🚗 Adaptive Cruise Control

Adaptive Cruise Control is an advanced form of cruise control in which the vehicle automatically adjusts its speed according to the vehicle ahead.

The system developed in this project consists of:

- Lead vehicle
- Ego vehicle
- Desired vehicle speed
- Safe following-distance calculation
- ACC decision logic
- PI controller
- Acceleration and braking limits
- Vehicle-distance calculation
- Simulation monitoring

### System Workflow

```text
Lead Vehicle Speed
        │
        ▼
┌─────────────────┐
│   ACC Logic     │◄──── Ego Vehicle Speed
└────────┬────────┘
         │
         ▼
    Target Speed
         │
         ▼
    Speed Error
         │
         ▼
┌─────────────────┐
│  PI Controller  │
└────────┬────────┘
         │
         ▼
    Saturation
         │
         ▼
   Ego Vehicle
         │
         ├──────────► Ego Speed
         │
         ▼
   Relative Speed
         │
         ▼
 Distance Calculation
         │
         ▼
 Vehicle Distance
| Parameter                |   Value |
| ------------------------ | ------: |
| Vehicle Mass             | 1000 kg |
| Vehicle Drag Coefficient |      50 |
| Desired Speed            |  10 m/s |
| Simulation Time          |    30 s |
| Sample Time              |   0.1 s |
| Initial Vehicle Distance |    30 m |
| Minimum Safe Distance    |     8 m |
| Desired Time Gap         |   1.5 s |
| Proportional Gain (Kp)   |     1.5 |
| Integral Gain (Ki)       |     0.3 |
| Maximum Acceleration     |  3 m/s² |
| Maximum Braking          | -4 m/s² |
| Time    | Lead Vehicle Speed |
| ------- | -----------------: |
| 0–10 s  |              8 m/s |
| 10–20 s |              6 m/s |
| 20–30 s |              9 m/s |
📐 Safe Following Distance

The ACC system calculates the safe following distance using the ego vehicle speed.

Safe Distance = Minimum Distance + Time Gap × Ego Vehicle Speed

For this project:

Minimum Distance = 8 m
Time Gap = 1.5 s

Therefore:

Safe Distance = 8 + 1.5 × Ego Vehicle Speed

The calculated safe distance is continuously compared with the actual distance between the lead vehicle and the ego vehicle.

🧠 ACC Decision Logic

The ACC decision logic determines the target speed based on the difference between the actual vehicle distance and the safe following distance.

Operating Conditions
When the lead vehicle is sufficiently far away, the ego vehicle maintains the desired speed.
When the ego vehicle approaches the safe following distance, the target speed is reduced according to the lead vehicle speed.
When the ego vehicle is slightly inside the safe-distance region, the target speed is reduced further.
When the ego vehicle is too close to the lead vehicle, a stronger reduction in target speed is applied.

The resulting target speed is passed to the PI controller.

🎛️ PI Controller

A PI controller is used to control the ego vehicle speed.

The controller parameters are:

Kp = 1.5
Ki = 0.3

The speed error is calculated as:

Speed Error = Target Speed - Ego Vehicle Speed

The PI controller generates the control action required for the ego vehicle to follow the target speed.

⚙️ Acceleration and Braking Limits

The controller output is limited using a saturation block.

Maximum Acceleration = 3 m/s²
Maximum Braking      = -4 m/s²
📈 MATLAB Simulation Results
1. Vehicle Speed

The vehicle-speed graph shows the desired speed, lead vehicle speed, and ego vehicle speed.

Screenshot: vehical_speed.png

View vehical_speed.png

2. Safe Following Distance

The graph compares the actual distance between the vehicles with the calculated safe following distance.

Screenshot: save_following_distance.png

View save_following_distance.png

3. Control Action

The control-action graph shows the acceleration and braking response generated by the ACC controller.

Screenshot: control_action.png

View control_action.png

4. Target Speed vs Ego Vehicle Speed

This graph shows the adaptive ACC target speed and the resulting ego vehicle speed.

Screenshot: target_speed_vs_ego_speed.png

View target_speed_vs_ego_speed.png

🔄 Simulink Implementation

The complete Adaptive Cruise Control system is implemented in Simulink using discrete-time blocks.

The Simulink model contains:

Desired Speed Constant
Lead Vehicle Speed input
ACC MATLAB Function block
Speed Error Sum
Proportional Gain
Integral Gain
Discrete-Time Integrator
PI Controller
Saturation
Ego Vehicle Speed Integrator
Relative Speed calculation
Vehicle Distance Integrator
Safe Distance calculation
Distance Error calculation
Simulink Scopes
Simulink Model
Screenshot: simulink_model.png

View simulink_model.png

💻 MATLAB Implementation

The MATLAB implementation performs the complete ACC simulation using numerical calculations.

The MATLAB script includes:

Vehicle parameter definition
Simulation parameter definition
Lead vehicle speed generation
Safe following-distance calculation
ACC decision logic
PI controller implementation
Acceleration and braking saturation
Ego vehicle speed calculation
Vehicle-distance calculation
Target-speed calculation
Simulation plots
Final simulation results
Safety-distance check
MATLAB Code and Output
Screenshot: code_and_output (2).png

View code_and_output (2).png

🔄 MATLAB and Simulink Workflow
Vehicle Parameters
        ↓
Simulation Parameters
        ↓
Lead Vehicle Speed Profile
        ↓
Safe Following Distance
        ↓
ACC Decision Logic
        ↓
Target Speed
        ↓
Speed Error
        ↓
PI Controller
        ↓
Acceleration / Braking Saturation
        ↓
Ego Vehicle Speed
        ↓
Relative Speed
        ↓
Vehicle Distance
        ↓
Distance Error
        ↓
Simulation Results
🧪 Simulation Output

The MATLAB simulation produced the following final values:

Desired Speed            = 10.00 m/s
Final Ego Vehicle Speed  = 9.01 m/s
Final Lead Vehicle Speed = 9.00 m/s
Final Vehicle Distance   = 21.61 m
Final Safe Distance      = 21.51 m

The implemented simulation safety check reported:

ACC Safety Check: Safe following distance maintained.

The safety check uses a 0.5 m numerical tolerance.

📊 Results Summary
Parameter	Final Value
Desired Speed	10.00 m/s
Final Ego Vehicle Speed	9.01 m/s
Final Lead Vehicle Speed	9.00 m/s
Final Vehicle Distance	21.61 m
Final Safe Distance	21.51 m
📁 Project Structure
Adaptive-cruise-control-matlab-simulink/
│
├── README.md
├── Adaptive_Cruise_Control.m
├── Adaptive_Cruise_Control.slx
│
├── code_and_output (2).png
├── control_action.png
├── save_following_distance.png
├── simulink_model.png
├── target_speed_vs_ego_speed.png
└── vehical_speed.png
📸 Project Screenshots

All six screenshots used in this project are included below.

1. code_and_output (2).png

https://github.com/parthkonde1273/Adaptive-cruise-control-matlab-simulink/blob/main/code_and_output%20%282%29.png

2. control_action.png

https://github.com/parthkonde1273/Adaptive-cruise-control-matlab-simulink/blob/main/control_action.png

3. save_following_distance.png

https://github.com/parthkonde1273/Adaptive-cruise-control-matlab-simulink/blob/main/save_following_distance.png

4. simulink_model.png

https://github.com/parthkonde1273/Adaptive-cruise-control-matlab-simulink/blob/main/simulink_model.png

5. target_speed_vs_ego_speed.png

https://github.com/parthkonde1273/Adaptive-cruise-control-matlab-simulink/blob/main/target_speed_vs_ego_speed.png

6. vehical_speed.png

https://github.com/parthkonde1273/Adaptive-cruise-control-matlab-simulink/blob/main/vehical_speed.png
