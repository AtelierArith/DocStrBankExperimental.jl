```
fixed(H::Homotopy; compile::Union{Bool,Symbol} = mixed)
```

`compile = :all` の場合は [`CompiledHomotopy`](@ref) を、`compile = :none` の場合は [`InterpretedHomotopy`](@ref) を、`compile = :mixed` の場合は [`MixedHomotopy`](@ref) を構築します。
