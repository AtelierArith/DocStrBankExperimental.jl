```
cartesian_indices(A)
cartesian_indices((n1, n2, ...))
cartesian_indices((i1:j1, i2:j2, ...))
cartesian_indices(CartesianIndex(i1, i2, ...), CartesianIndex(j1, j2, ...))
cartesian_indices(R)
```

all yield an instance of `CartesianIndices` suitable for multi-dimensional indexing of respectively: all the indices of array `A`, a multi-dimensional array of dimensions `(n1,n2,...)`, a multi-dimensional region whose first and last indices are `(i1,i2,...)` and `(j1,j2,...)` or a Cartesian region defined by `R`, an instance of `CartesianIndices`.
