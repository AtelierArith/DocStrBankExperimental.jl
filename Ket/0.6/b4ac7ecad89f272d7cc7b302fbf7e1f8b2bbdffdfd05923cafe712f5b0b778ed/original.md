```
permute_systems(X::AbstractMatrix, perm::Vector, dims::Matrix)
```

Permutes the order of the subsystems of the matrix `X`, which is composed by subsystems of dimensions `dims`, according to the permutation `perm`. `dims` should be a n × 2 matrix where `dims[i, 1]` is the number of rows of subsystem i, and `dims[i, 2]` is its number of columns.
