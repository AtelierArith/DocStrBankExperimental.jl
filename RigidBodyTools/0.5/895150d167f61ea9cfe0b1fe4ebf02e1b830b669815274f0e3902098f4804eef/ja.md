```
SmoothVelocityRampDOF(ẍ0,ẋ1,ẋ2,t0[;ramp=EldredgeRamp(11.0)]) <: AbstractPrescribedDOFKinematics
```

`ẋ1`から`ẋ2`への滑らかな速度変化を`ẍ0`の名目加速度で`t0`から開始する運動学。`ẍ0`の符号は`ẋ2-ẋ1`の符号と同じである必要があり、異なる場合は自動的に変更されます。オプションのramp引数は、滑らかさの係数が11の滑らかなランプ`EldredgeRamp`によって与えられると仮定されています（大きな値はランプのオン/オフの遷移を鋭くします）が、異なる値の別のEldredgeランプに置き換えることができます。
