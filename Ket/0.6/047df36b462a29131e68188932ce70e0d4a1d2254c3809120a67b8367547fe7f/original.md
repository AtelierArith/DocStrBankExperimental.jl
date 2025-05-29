```
permute_systems(X::AbstractMatrix, perm::AbstractVector, dims::AbstractVector = _equal_sizes(X))
```

Permutes the order of the subsystems of the square matrix `X`, which is composed by square subsystems of dimensions `dims`, according to the permutation `perm`. If the argument `dims` is omitted two equally-sized subsystems are assumed.
