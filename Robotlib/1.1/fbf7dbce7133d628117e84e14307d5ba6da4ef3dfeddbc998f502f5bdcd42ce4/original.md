```
calib_force_eigen(POSES, F)
```

`POSES` ∈ ℜ(4,4,N) or ℜ(3,3,N) are the orientations of the tool frame from the robot forward kinematics, 4×4 transformation matrices or 3×3 rotation matrices. `F` ∈ ℜ(N,3) vector of forces (accepts ℜ(N×6) matrix with torques also)

# Usage

```
Rf*force[i,1:3] + forceoffs = POSES[1:3,1:3,i]'*[0, 0, mf*-9.82]
```
