```
global_adjacencies(M::Matrix{T}, idx::Union{NTuple{N, Int}, CartesianIndex{N}}, ignored_elem::T)
```

Returns the "globally" adjacent indices in arbitrary positions in the cardinal directions from a specified index in matrix `M`, ignoring certain adjacent elements (i.e., skipping over them).
