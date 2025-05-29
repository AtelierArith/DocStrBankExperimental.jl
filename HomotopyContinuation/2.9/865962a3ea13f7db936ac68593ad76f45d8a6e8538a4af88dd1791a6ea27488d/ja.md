```
fix_parameters(H::Union{Homotopy,AbstractHomotopy}, p; compile::Union{Bool,Symbol} = mixed)
```

与えられたホモトピー `H` のパラメータを固定します。[`FixedParameterHomotopy`](@ref) を返します。
