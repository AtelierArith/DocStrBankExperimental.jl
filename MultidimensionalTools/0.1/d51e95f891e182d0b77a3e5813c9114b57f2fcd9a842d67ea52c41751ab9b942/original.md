```
global_n_adjacent_to(M::Array{T, N},idx::Union{NTuple{N, Int}, CartesianIndex{N}}, adj_elem::T) where {N, T}
```

Given a matrix M, counts the number of adjacent elements to index `idx` that are exactly the `adj_elem`, skipping over certain elements if needed (see `expanded_adjacencies`).
