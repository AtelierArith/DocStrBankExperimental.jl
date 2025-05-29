```julia
mutable struct CartesianSTM{F} <: StaticArraysCore.FieldMatrix{6, 6, F}
```

6自由度のカルテジアン状態遷移行列のためのラベル付き可変行列。
