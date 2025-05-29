```
pathbetween(N::SpeciesInteractionNetwork{<:Partiteness{T}, <:Interactions}, source::T, target::T) where {T}
```

Returns the path between `source` and `target`, using [`BellmanFord`](@ref) as the default algorithm.
