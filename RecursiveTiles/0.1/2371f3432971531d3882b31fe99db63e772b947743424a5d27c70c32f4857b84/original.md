```
AbstractTile{P,T,U,S,N} <: AbstractVector{T}
```

Supertype for tile abstraction, which is a struct containing an `P<:AbstractVector{T}` and an index `U<:Tuple{Vararg{S,N}}`.
