```
T_TF_S, meanRMS,RMS, norms = calibNAXP(points_S, lines_S, POSES, T_TF_S, planes::AbstractVector{Int},  iters = 50; doplot=false)
```

This functions implements the algorithm from the paper "Six DOF eye-to-hand calibration from 2D measurements using planar constraints" which solves the problem `Prb = n'A(X*Ps)` Extensions to the algorithm were developed in the thesis "Machine Learning and System Identification for Estimation in Physical Systems" Chapter 13.2 and appendices. https://lup.lub.lu.se/search/publication/ffb8dc85-ce12-4f75-8f2b-0881e492f6c0

If result is bad, check if you send data in correct form

`POSES ∈ R(4,4,N)` is always the position of the tool frame from the robot FK

`points_S ∈ R(3,N)` are measurements from a line laser scanner. Given in the sensor frame. This script assumes that the laser plane is the sensor XY plane with y-axis pointing outwards from the sensor.

`lines_S ∈ R(3,N)` are vectors corresponding to the direction of the measured laser line `planes ∈ Z(N)` is a vector of indices corresponding to which plane a mesurement comes from. It must be same length as `points_S` and enumerate the planes starting at 1. Example (N=15, number of planes = 3): [1,1,1,1,1,2,2,2,2,2,3,3,3,3,3]

`iters` determines the number of iterations

@inproceedings{carlson2015six,   title={Six DOF eye-to-hand calibration from 2D measurements using planar constraints},   author={Carlson, Fredrik Bagge and Johansson, Rolf and Robertsson, Anders},   booktitle={Intelligent Robots and Systems (IROS), 2015 IEEE/RSJ International Conference on},   pages={3628–3632},   year={2015},   organization={IEEE} }
