```julia
mutable struct OrbitalElements{F} <: AstrodynamicalModels.AstrodynamicalState{F, 6}
```

6自由度のケプラー状態のためのラベル付き可変ベクトル。
