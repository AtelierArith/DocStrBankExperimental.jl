```
fixed(H::Homotopy; compile::Union{Bool,Symbol} = mixed)
```

Constructs either a [`CompiledHomotopy`](@ref) (if `compile = :all`), an [`InterpretedHomotopy`](@ref) (if `compile = :none`) or a [`MixedHomotopy`](@ref) (`compile = :mixed`).
