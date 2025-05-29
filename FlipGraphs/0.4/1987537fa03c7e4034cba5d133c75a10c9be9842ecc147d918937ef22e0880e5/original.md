```
multi_adjacency_matrix_deltacomplex(D::DeltaComplex) :: Matrix{Int32}
```

Compute the multi *adjacency matrix* of the delta complex `D`.

The `i,j`-th value counts the number of sides through which the `i`-th and `j`-th `TriFace` are adjacent.
