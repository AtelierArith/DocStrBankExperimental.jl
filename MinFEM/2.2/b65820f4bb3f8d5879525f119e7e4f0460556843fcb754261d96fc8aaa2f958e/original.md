```
assemble_laplacian(
    mesh::Mesh;
    qdim::Int64 = 1
) -> SparseMatrixCSC{Float64, Int64}
```

Returns the Laplacian stiffness matrix for all elements of mesh and qdim components.
