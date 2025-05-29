```
T_RB_T, T_TF_TCP, normDist = calibAXYB(POSES, MEASURED; ortho=true, estimator = \, refine = true)
```

This functions solves the problem AX = YB

  * `POSES` is always the position of the tool frame from the robot FK
  * `MEASURED` is the position of the object mounted on the tool frame, for   instance if measuring with the Nikon it is the diod frame. If measuring   with a laser scanner mounted on the TF, it is the position of the SCANNER   in the measured object frame, not the object in the scanner frame!
  * `ortho` is a flag indicating if found matrices are to be orthogonalized
  * `refine`: run a second, local optimization routine to improve the accuracy (recommended)
