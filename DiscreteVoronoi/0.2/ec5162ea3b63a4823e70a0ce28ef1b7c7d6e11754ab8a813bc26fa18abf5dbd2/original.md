```
jfa_voronoi!(grid::Matrix{T}, sites::Vector{T}; distance=euclidean) where {T<:SVector{2,Int}}
```

Construct in-place a Voronoi diagram using the [jump flooding algorithm](https://en.wikipedia.org/wiki/Jump_flooding_algorithm). The algorithm assumes that a blank cell in the grid has value `SVector(0, 0)` and that sites are inside the grid.
