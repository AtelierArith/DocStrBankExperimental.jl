```
expanded_adjacencies(M::Array{T, N}, expand_by::T, idx::Union{NTuple{N, Int}, CartesianIndex{N}})
```

`expanded_adjacencies` will get all adjacencies of an index in the matrix M, given that the matrix is infinitely expanding by a single element beyond the specified M.  See also `reshape_as_required`.
