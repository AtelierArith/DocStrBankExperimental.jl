```
permute_systems(X::AbstractVector, perm::AbstractVector, dims::AbstractVector = _equal_sizes(X))
```

Permutes the order of the subsystems of vector `X` with subsystem dimensions `dims` according to the permutation `perm`. If the argument `dims` is omitted two equally-sized subsystems are assumed.
