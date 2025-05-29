```
SmoothRampDOF(ẋ0,Δx,t0[;ramp=EldredgeRamp(11.0)]) <: AbstractPrescribedDOFKinematics
```

Kinematics describing a smooth ramp change in position `Δx` starting at time `t0` with nominal rate `ẋ0`. Note that the sign of `ẋ0` should be the same as the sign of `Δx`, and will be automatically changed if they differ. The optional ramp argument is assumed to be given by the smooth ramp `EldredgeRamp` with a smoothness factor of 11 (larger values lead to sharper transitions on/off the ramp), but this can be replaced by another Eldredge ramp with a different value or a `ColoniusRamp`.
