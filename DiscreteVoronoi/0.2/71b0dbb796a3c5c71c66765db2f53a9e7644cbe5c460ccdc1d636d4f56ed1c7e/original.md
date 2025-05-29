```
dac_voronoi!(grid::Matrix{T}, sites::Vector{T}; distance=euclidean) where {T<:SVector{2,Int}}
```

Construct in-place a Voronoi diagram using the [divide-and-conquer algorithm](https://doi.org/10.1109%2Feit48999.2020.9208270).
