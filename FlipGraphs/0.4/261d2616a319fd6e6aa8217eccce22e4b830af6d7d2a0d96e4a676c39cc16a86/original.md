```
multi_adjacency_matrix_triangulation(D::DeltaComplex) :: Matrix{Int32}
```

Compute the *adjacency matrix* of the multigraph of the triangulation defined by `D`.

The $i,j$-th entry notes the number of edges that connect these two points.

See also [`adjacency_matrix_triangulation`](@ref)
