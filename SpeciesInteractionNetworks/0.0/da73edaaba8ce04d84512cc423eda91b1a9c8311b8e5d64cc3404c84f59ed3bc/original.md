```
render(::Type{Probabilistic{T}}, N::SpeciesInteractionNetwork{<:Partiteness, <:Interactions}) where {T <: AbstractFloat}
```

Returns a probabilistic version of the network, where interaction probabilities have the type `T`. This can be used to convert a probabilistic network into a different number representation.
