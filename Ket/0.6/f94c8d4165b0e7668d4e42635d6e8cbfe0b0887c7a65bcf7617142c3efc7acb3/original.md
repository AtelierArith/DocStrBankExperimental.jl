```
permutation_matrix(dims::Union{Integer,AbstractVector}, perm::AbstractVector)
```

Unitary that permutes subsystems of dimension `dims` according to the permutation `perm`. If `dims` is an Integer, assumes there are `length(perm)` subsystems of equal dimensions `dims`.
