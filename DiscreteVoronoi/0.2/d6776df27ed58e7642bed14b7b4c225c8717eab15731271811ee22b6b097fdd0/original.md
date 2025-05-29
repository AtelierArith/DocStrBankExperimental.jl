```
redac_voronoi!(grid::Matrix{T}, sites::Vector{T}; distance=euclidean, auxiliary=exact_aux) where {T<:SVector{2,Int}}
```

Performs a divide-and-conquer method similar to `dac_voronoi!` but has an additional site-elimination step which aims to reduce the work of subsequent steps.
