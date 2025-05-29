```julia
abstract type LinearMode <: Causal.BufferMode
```

線形バッファモードの抽象型。 [`Normal`](@ref)、[`Lifo`](@ref)、[`Fifo`](@ref)を参照してください。
