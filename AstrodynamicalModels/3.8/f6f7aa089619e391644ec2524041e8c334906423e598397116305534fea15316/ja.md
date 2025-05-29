```julia
mutable struct AttitudeState{F} <: AstrodynamicalModels.AstrodynamicalState{F, 7}
```

姿勢力学のための可変状態ベクトル。
