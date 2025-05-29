```
fixed(F::System; compile::Union{Bool,Symbol} = mixed)
```

Constructs either a [`CompiledSystem`](@ref) (if `compile = :all`), an [`InterpretedSystem`](@ref) (if `compile = :none`) or a [`MixedSystem`](@ref) (`compile = :mixed`).
