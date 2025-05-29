```
naive_voronoi!(grid::Matrix{T}, sites::Vector{T}; distance=euclidean) where {T<:SVector{2,Int}}
```

Construct in-place a Voronoi diagram in the most basic way possible: check every cell and every combination.
