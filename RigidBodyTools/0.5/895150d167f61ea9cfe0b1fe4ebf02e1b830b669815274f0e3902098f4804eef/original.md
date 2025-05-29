```
SmoothVelocityRampDOF(ẍ0,ẋ1,ẋ2,t0[;ramp=EldredgeRamp(11.0)]) <: AbstractPrescribedDOFKinematics
```

Kinematics describing a smooth ramp change in velocity from `ẋ1` to `ẋ2` starting at time `t0` with nominal acceleration `ẍ0`. Note that the sign of `ẍ0` should be the same as the sign of `ẋ2-ẋ1`, and will be automatically changed if they differ. The optional ramp argument is assumed to be given by the smooth ramp `EldredgeRamp` with a smoothness factor of 11 (larger values lead to sharper transitions on/off the ramp), but this can be replaced by another Eldredge ramp with a different value.
