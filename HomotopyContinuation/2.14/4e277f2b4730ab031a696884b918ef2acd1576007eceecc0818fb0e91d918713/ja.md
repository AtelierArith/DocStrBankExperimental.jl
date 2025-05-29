```
fix_parameters(F::Union{System,AbstractSystem}, p; compile::Union{Bool,Symbol} = mixed)
```

与えられたシステム `F` のパラメータを固定します。 [`FixedParameterSystem`](@ref) を返します。
