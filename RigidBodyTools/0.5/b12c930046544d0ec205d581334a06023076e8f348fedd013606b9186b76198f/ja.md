```
OscillatoryDOF(amp,angfreq,phase,ẋ0) <: AbstractPrescribedDOFKinematics
```

振幅 `amp`、角周波数 `angfreq`、位相 `phase`、および平均速度 `ẋ0` を持つ正弦波運動を設定します。提供される関数は `x(t) = ẋ0*t + amp*sin(angfreq*t+phase)` です。
