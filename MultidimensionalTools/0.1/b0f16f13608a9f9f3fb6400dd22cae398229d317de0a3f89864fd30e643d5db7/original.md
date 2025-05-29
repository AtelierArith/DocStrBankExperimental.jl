```
n_adjacent_to(M::Array{T, N}, idx::Union{NTuple{N, Int}, CartesianIndex{N}}, adj_elem::T)
```

Given a matrix M, counts the number of adjacent elements to index `idx` that are exactly the `adj_elem`.
