```julia
mutable struct QuantumFlag{F<:FlagSOS.Flag, T}
```

タイプ `F` のフラグの線形結合で、タイプ `T` の係数を持ちます。
