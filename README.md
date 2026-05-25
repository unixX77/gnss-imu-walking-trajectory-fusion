# GNSS-IMU-WALKING-TRAJECTORY-FUSION
A preprocessing and Kalman-filter-based trajectory estimation pipeline for smartphone walking data

# Project Overview:
This project develops a GNSS–IMU preprocessing and trajectory-estimation pipeline for smartphone-based walking data. The main goal is to analyze the reliability of raw mobility signals, identify sensor-related issues, and prepare the data for robust trajectory estimation and digital biomarker analysis.

The pipeline uses GNSS position data, IMU acceleration and gyroscope signals, orientation measurements, step information, and continuous reference distance. The raw GNSS data is converted into local metric coordinates, compared against reference walking distance, and analyzed for position jumps, unrealistic movement, and confidence-related errors. Candidate GNSS outliers are detected using physically interpretable criteria such as step distance, computed speed, GNSS-reported speed, and confidence interval. 
In parallel, the IMU signals are inspected for acceleration patterns, gyroscope activity, timing gaps, phone-orientation effects, and suspicious high-motion regions. Instead of blindly deleting unreliable measurements, the project keeps raw sensor data intact and creates quality flags that can later be used to skip or down-weight unreliable updates during filtering.

Finally, the project implements a first-stage Kalman-filter-based trajectory estimation prototype using a constant-velocity motion model and valid GNSS position updates. This prototype demonstrates how GNSS quality control can be integrated into a sensor-fusion pipeline and provides a foundation for future EKF-based GNSS/IMU fusion using orientation-corrected acceleration and adaptive noise modeling.

# Motivation
Reliable walking trajectory estimation is an important step before extracting meaningful mobility-based features from smartphone sensor data. Applications such as digital biomarker analysis, mobility monitoring, and early cognitive-decline research often depend on accurate information about how a person moves through space, including walking distance, speed changes, pauses, turns, and trajectory smoothness.

However, raw smartphone sensor data is often noisy and unreliable. GNSS measurements can contain position jumps, high uncertainty, missing speed or heading values, and cumulative distance errors. In this project, the raw GNSS trajectory showed that even a short early position jump can significantly inflate the total estimated walking distance compared with the reference distance.

The motivation of this project is to build a structured preprocessing and quality-control pipeline that identifies these issues before trajectory estimation. By detecting unreliable GNSS measurements, analyzing IMU signal behavior, and using a Kalman-filter-based trajectory estimation prototype, this project demonstrates how smartphone GNSS/IMU data can be prepared for more reliable mobility analysis and future EKF-based sensor fusion.
