```
fixed(F::System; compile::Union{Bool,Symbol} = mixed)
```

`compile = :all` の場合は [`CompiledSystem`](@ref) を、`compile = :none` の場合は [`InterpretedSystem`](@ref) を、また `compile = :mixed` の場合は [`MixedSystem`](@ref) を構築します。
