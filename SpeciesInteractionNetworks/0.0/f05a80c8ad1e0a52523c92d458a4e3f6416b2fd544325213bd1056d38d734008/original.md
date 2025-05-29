```
pathbetween(::Type{ShortestPathMethod}, N::SpeciesInteractionNetwork{<:Partiteness{T}, <:Interactions}, source::T, target::T) where {T}
```

Returns the path between `source` and `target`. The result is given as a vector of interactions, *i.e.* it gives the subset of the output of `interactions(N)` going from `source` to `target`.
