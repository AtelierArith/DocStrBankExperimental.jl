```
Rf, g, m = calib_force_eigen(POSES, F, g)
```

`POSES` ∈ ℜ(4,4,N) or ℜ(3,3,N) are the orientations of the tool frame from the robot forward kinematics, 4×4 transformation matrices or 3×3 rotation matrices. `F` ∈ ℜ(N,3) vector of forces (accepts ℜ(N×6) matrix with torques also) ´g´ is an initial guess for the gravity vector.

# Usage

```
Rf*force[i,1:3] = POSES[1:3,1:3,i]'*g
```

See also `calib_force_eigen`.
