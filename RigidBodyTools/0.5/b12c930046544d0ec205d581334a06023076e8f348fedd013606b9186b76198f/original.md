```
OscillatoryDOF(amp,angfreq,phase,ẋ0) <: AbstractPrescribedDOFKinematics
```

Set sinusoidal kinematics with amplitude `amp`, angular frequency `angfreq`, phase `phase`, and mean velocity `ẋ0`. The function it provides is `x(t) = ẋ0*t + amp*sin(angfreq*t+phase)`.
