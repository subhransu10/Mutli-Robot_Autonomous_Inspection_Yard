# Multi-Robot Autonomous Inspection Yard Project

**Platform:** Unity 2022.3.62f3  
**Robots:** Two Clearpath Husky A200 Mobile Robots  
**Project Duration:** 4–5 weeks  
**Environment:** Industrial Inspection Yard

## 1. Project Overview

The objective of this project is to develop a multi-robot autonomous inspection system using two Clearpath Husky A200 mobile robots in a simulated industrial environment.

The provided Unity environment includes two warehouses, containers, a generator, a loading area, roads, vehicles, pedestrians, and two Husky robots (H1 and H2).

Students will implement functionalities related to autonomous inspection, obstacle avoidance, robot-to-robot coordination, and dynamic task allocation.

The goal is **to extend the existing environment and develop a cooperative robotic inspection system rather than build a new simulation from scratch**.

*[Insert Screenshot 1: Overview of the Inspection Yard with both Husky robots and checkpoints]*

## 2. Getting Started

### 2.1 Project Setup

1. Download and install **Unity 2022.3.62f3** using [Unity Hub](https://unity.com/download).
2. Download the project from this [OneDrive link](). Request access from the instructor if necessary.
3. Open the provided Unity project and load the Inspection Yard scene.

### 2.2 Required Packages

Once the project is loaded, open **Window → Package Manager** and check whether the following packages are installed.

**A. URDF Importer (if required)**

1. Click **+ → Add package from git URL**.
2. Enter:

   `https://github.com/Unity-Technologies/URDF-Importer.git?path=/com.unity.robotics.urdf-importer#v0.5.2`

3. Click **Add**.

**B. Unity glTFast (if required)**

1. Click **+ → Add package by name**.
2. Enter `com.unity.cloud.gltfast`.
3. Click **Add**.

**C. Universal Render Pipeline (URP)**

1. In Package Manager, search for **Universal RP** and install it if missing.
2. Check whether a URP Asset already exists in the Project window.
3. If necessary, create one using **Create → Rendering → URP Asset (with Universal Renderer)**.
4. Assign the URP Asset under **Edit → Project Settings → Graphics**.
5. Verify the active pipeline under **Project Settings → Quality**.

**Note:** Do not replace existing pipeline settings or reinstall packages that are already correctly configured.

*[Insert Screenshot 2: Package Manager and Unity project settings]*

### 2.3 Unity Project Structure

Familiarize yourself with the **Scene, Hierarchy, Inspector, and Project** windows.

Locate the following objects:

| Object / Component | Description |
|---|---|
| Husky 1 (H1) | First inspection robot |
| Husky 2 (H2) | Second inspection robot |
| Warehouse A / B | Industrial inspection locations |
| Containers | Inspection areas and shared narrow corridor |
| Checkpoints A–F | Six predefined inspection locations |
| Vehicles | Static and dynamic obstacles |
| Pedestrians | Moving obstacles |
| Spawn Points | Initial and final robot positions |

**Note:** Some objects may be located under child GameObjects. Students may reuse existing models, prefabs, and movement scripts.

*[Insert Screenshot 3: Unity Hierarchy showing robots, checkpoints, and environment objects]*

## 3. Inspection Mission

The inspection yard contains **six checkpoints**, distributed between the two robots.

| Checkpoint | Inspection Location | Assigned Robot |
|---|---|---|
| A | Generator | Husky 1 |
| B | Warehouse A | Husky 1 |
| C | Western Container | Husky 1 |
| D | Eastern Container | Husky 2 |
| E | Warehouse B | Husky 2 |
| F | Loading Area | Husky 2 |

### Expected Mission Sequence

1. **Mission Start:** Both robots begin at their respective spawn points and receive their assigned inspection tasks.
2. **Autonomous Inspection:** Each robot navigates to its assigned checkpoints and records successful inspections.
3. **Pedestrian Avoidance:** A pedestrian crosses the robot's path. The approaching robot slows down or stops to avoid a collision.
4. **Robot-to-Robot Coordination:** Both robots approach the narrow container corridor. Only one robot may enter at a time, while the other waits.
5. **Dynamic Task Reassignment:** A vehicle blocks Husky 1's route. The coordinator evaluates whether an unfinished task can be reassigned to Husky 2.
6. **Mission Completion:** Both robots return to their spawn points. The system records completed tasks, travel times, delays, and safety events.

## 4. Student Tasks

The project is divided into four modules. Each student is responsible for developing and testing an assigned functionality.

### Student 1 — Autonomous Navigation and Inspection

**Objective:** Implement autonomous navigation and checkpoint-based inspection for both Husky robots.

**Tasks:**
- Implement basic robot movement using differential-drive kinematics.
- Define navigation paths or waypoints connecting the inspection locations.
- Enable both Huskies to navigate autonomously to assigned checkpoints.
- Implement checkpoint arrival detection and inspection completion status.
- Implement return-to-start behavior after completing the mission.

**Expected Result:** Both Huskies can autonomously navigate between checkpoints, record inspections, and return to their starting positions.

**Note:** A simple waypoint-following algorithm is sufficient. Implementing a complete SLAM or advanced path-planning system is not required.

### Student 2 — Dynamic Obstacle Detection and Safety

**Objective:** Enable the robots to operate safely around pedestrians, vehicles, and other obstacles.

**Tasks:**
- Use the provided pedestrian and vehicle models to create dynamic scenarios.
- Implement obstacle detection using raycasts, trigger colliders, or simulated sensor data.
- Define safety zones around the robots.
- Implement slowing or stopping when an obstacle approaches or blocks a robot's path.
- Visualize detected obstacles and safety warnings.

**Expected Result:** Both robots can detect nearby obstacles and respond appropriately to avoid collisions.

**Note:** Training an object detection model is not required. Unity's built-in physics and simulated detections may be used.

### Student 3 — Multi-Robot Coordination and Shared Passage

**Objective:** Implement coordination between the two Huskies when accessing shared or restricted areas.

**Tasks:**
- Define the narrow corridor between the containers as a shared passage.
- Implement a simple permission-based system allowing only one robot inside at a time.
- Make the second robot wait until the passage becomes available.
- Implement basic robot status communication (e.g., waiting, moving, occupying corridor).
- Prevent collisions and deadlocks when both robots request access simultaneously.

**Expected Result:** Both Huskies safely negotiate the narrow corridor without entering simultaneously or blocking each other.

**Note:** A simple centralized permission system or shared-state mechanism is sufficient. Advanced multi-agent planning is not required.

### Student 4 — Dynamic Task Allocation and Mission Monitoring

**Objective:** Manage inspection assignments and monitor the progress of the cooperative mission.

**Tasks:**
- Implement a basic mission coordinator that assigns inspection checkpoints to both robots.
- Track the status of each inspection task (pending, in progress, completed, or blocked).
- Implement simple task reassignment when a robot cannot reach its assigned checkpoint.
- Develop a basic interface displaying robot status and inspection progress.
- Record mission statistics such as completed checkpoints, travel times, waiting times, and safety events.

**Expected Result:** A mission management system capable of tracking both robots, reallocating unfinished tasks when necessary, and reporting overall mission performance.

**Note:** Rule-based task allocation is sufficient. Complex optimization or reinforcement learning is not required.

*[Insert Screenshot 4: Inspection checkpoints, corridor, and mission visualization]*

## 5. General Requirements

- Use the provided Unity project and the two existing Husky robot models.
- Keep implementations modular and clearly named to simplify evaluation.
- Avoid unnecessary changes to unrelated components.
- Ensure that the implemented functionalities work correctly in Unity Play mode.
- Students may use simulated sensing and predefined navigation data.
- Coordinate with other students to ensure compatibility between modules.
- The final integrated system should demonstrate cooperation between both robots.

## 6. Evaluation and Grading

Each module will be graded out of **100 points**.

| Criteria | Points |
|---|---:|
| Correct implementation of assigned tasks | 30 |
| Functionality and integration | 25 |
| Code organization and explanation | 20 |
| Final demonstration | 25 |
| **Total** | **100** |

## 7. Final Submission

Each student must submit:

1. **Unity Implementation:** Completed scripts, modified assets, and relevant project files.
2. **Demonstration Videos:** A short individual demonstration (2–3 minutes) and a combined working prototype video (no fixed time limit).
3. **Final Presentation and Report:** A concise explanation of the implementation, testing, results, and limitations.

The combined prototype should demonstrate the six mission stages described in Section 3.

**Important:** Evaluation will focus on correct functionality, integration with the provided project, and the student's understanding of their implementation. Unnecessary complexity is not expected.

## 8. Project Demo

A demonstration of the provided Inspection Yard environment.

*[Insert the GitHub video attachment URL here.]*
