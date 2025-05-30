```
SmoothRampDOF(ẋ0,Δx,t0[;ramp=EldredgeRamp(11.0)]) <: AbstractPrescribedDOFKinematics
```

位置 `Δx` の滑らかな ramp 変化を時間 `t0` で開始し、名目速度 `ẋ0` で記述する運動学。`ẋ0` の符号は `Δx` の符号と同じである必要があり、異なる場合は自動的に変更されます。オプションの ramp 引数は、滑らかさの係数が 11 の滑らかな ramp `EldredgeRamp` によって与えられると仮定されています（大きな値は ramp のオン/オフの遷移を鋭くします）が、別の値の別の Eldredge ramp または `ColoniusRamp` に置き換えることができます。
