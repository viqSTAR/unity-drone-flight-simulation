# Drone Flight & Aerodynamic Wind Physics Simulation

A physics-driven flight simulation built in **Unity (C#)** featuring a 6-DOF quadcopter drone controller, counter-rotating propeller mechanics, and a real-time wind turbulence physics system.

---

## ✈️ Key Features & Technical Highlights

### 1. 6-DOF Quadcopter Flight Controller (`DroneController.cs`)
- **Physics-Based Hovering**: Applies continuous upward equilibrium force (`hoverForce = 19.62f`) in `FixedUpdate` balancing gravitational acceleration for realistic buoyancy.
- **Counter-Rotating Propellers**: Independently spins 4 quadcopter rotors in alternating clockwise/counter-clockwise directions at 2,500 RPM for rotational torque balance.
- **Thrust & Velocity Clamping**: Directional thrust vectors (`transform.forward` and `transform.right`) with linear velocity magnitude clamping to prevent runaway acceleration.
- **Orientation & Mouse Steering**: World-space yaw and local-space pitch rotation responding to mouse sensitivity.

### 2. Aerodynamic Wind Turbulence System (`DroneWindPhysics.cs`)
- **Directional Wind Forces**: Connects with Unity's `WindZone` to sample wind vector direction and main force magnitude.
- **Aerodynamic Tilt**:
  - Decomposes world wind vector into local coordinates via `transform.InverseTransformDirection`.
  - Dynamically calculates pitch and roll offsets (`Mathf.Clamp`).
  - Smoothly interpolates orientation using `Quaternion.Slerp` to simulate realistic turbulence resistance.

### 3. Environmental Physics & Instrumentation
- **Physical Interactions (`WindPhysicsObject.cs`)**: Propagates wind turbulence across floating and ground rigidbodies in the environment.
- **HUD & Telemetry (`WindUIController.cs`, `GameUi.cs`)**: Live readout of wind parameters and flight status.
- **Smooth Chase Camera (`CameraFollow.cs`)**: Dynamic offset follow camera dampening sharp rotational maneuvers.

---

## 📂 Project Structure

```
RealisticWorldSimulation/
├── Assets/
│   ├── Scripts/                    # Core flight & physics C# scripts
│   │   ├── DroneController.cs      # Quadcopter flight physics & controls
│   │   ├── DroneWindPhysics.cs     # Dynamic wind force & tilt mechanics
│   │   ├── WindPhysicsObject.cs    # Environmental physics integration
│   │   ├── WindUIController.cs     # HUD telemetry & instrumentation
│   │   ├── CameraFollow.cs         # Chase camera controller
│   │   └── GameUi.cs               # UI state management
│   ├── Forst/                      # Environmental props & terrain assets
│   ├── Material/                   # Shaders and materials
│   ├── Scenes/                     # Flight simulation scenes
│   ├── Settings/                   # Universal Render Pipeline (URP) assets
│   └── Skybox/                     # Atmospheric skyboxes
└── ProjectSettings/                # Input, Physics, and Tag configurations
```

---

## 🛠️ Built With

- **Unity 6 / 2022+** (Universal Render Pipeline)
- **C#** (RigidBody physics, Vector math, Quaternion rotations)

---

## 👤 Author

**Vikashdeep Prasad**  
GitHub: [@viqSTAR](https://github.com/viqSTAR)  
Portfolio: [vikashdeep-portfolio.vercel.app](https://vikashdeep-portfolio.vercel.app)
