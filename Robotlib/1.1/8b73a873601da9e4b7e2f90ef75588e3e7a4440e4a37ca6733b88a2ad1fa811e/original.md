```
Rf, m = calib_force(POSES, F, m0::Real = 0.3; offset=true)
Rf, m = calib_force(POSES, F, g::Vector; offset=true)
```

`POSES` ∈ ℜ(4,4,N) are the positions of the tool frame from the robot forward kinematics, 4x4 transformation matrices `F` ∈ ℜ(N,3) vector of forces (accepts ℜ(Nx6) matrix with torques also)

# Usage

```
Rf*force[i,1:3] + forceoffs = POSES[1:3,1:3,i]'*[0, 0, mf*-9.82]
```

If `m0` is supplied, it's assumed that the gravity vector is [0,0,-g], or in words, that the gravity is acting along the negative z axis. A custom gravity vector `g` can also be supplied.

This function can also be used to calibrate an accelerometer.

[Bagge Carlson, F.](https://www.control.lth.se/staff/fredrik-bagge-carlson/), ["Machine Learning and System Identification for Estimation in Physical Systems"](https://lup.lub.lu.se/search/publication/ffb8dc85-ce12-4f75-8f2b-0881e492f6c0) (PhD Thesis 2018).

See also `calib_force_iterative` and `calib_force_eigen`.
