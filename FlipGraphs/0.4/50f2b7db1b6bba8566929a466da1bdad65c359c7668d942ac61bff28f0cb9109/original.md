```
adjacency_matrix_triangulation(D::DeltaComplex) :: Matrix{Int32}
```

Compute the *simple adjacency matrix* of the triangulation defined by `D`.

All entries are either 0 or 1.

See also [`multi_adjacency_matrix_triangulation`](@ref)
