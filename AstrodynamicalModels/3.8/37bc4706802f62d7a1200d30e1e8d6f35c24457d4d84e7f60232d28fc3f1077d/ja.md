```julia
mutable struct CartesianState{F} <: AstrodynamicalModels.AstrodynamicalState{F, 6}
```

6自由度のカルテジアン状態のためのラベル付き可変ベクトルです。
