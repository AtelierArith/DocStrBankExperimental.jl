```
assemble_massmatrix(
    mesh::Mesh;
    qdim::Int64 = 1,
    order::Int64 = 1
) -> SparseMatrixCSC{Float64, Int64}
```

Returns the mass matrix with given local integration order for all elements  of mesh and qdim components.
