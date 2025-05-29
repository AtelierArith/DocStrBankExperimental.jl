```
global_adjacencies(M::Matrix{T}, idx::Union{NTuple{N, Int}, CartesianIndex{N}}, ignored_elem::T)
```

Using `global_adjacencies_indices`, returns the elements of each globally adjacent index.  This function is mainly used for `global_n_adjacent_to`.
