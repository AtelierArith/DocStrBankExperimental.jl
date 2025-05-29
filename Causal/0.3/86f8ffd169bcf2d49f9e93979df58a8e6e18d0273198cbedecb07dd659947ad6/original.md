```julia
abstract type LinearMode <: Causal.BufferMode
```

Abstract type of linear buffer modes. See [`Normal`](@ref), [`Lifo`](@ref), [`Fifo`](@ref)
