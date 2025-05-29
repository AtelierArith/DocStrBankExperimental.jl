```
Collection{T} <: AbstractVector{T}
```

A wrapper around a `Vector{T}`, that allows custom printing and dispatch rules of custom `T` (e.g., `AbstractIrrep` & `NewBandRep`).

In Crystalline, it is assumed that all elements of the wrapped vector are associated with the *same* space, point, or little group. Accordingly, if `T` implements [`dim`](@ref) or  [`num`](@ref), either must return the same value for each element of the `Collection` (and is equal to `dim(::Collection)` and `num(::Collection)`).
