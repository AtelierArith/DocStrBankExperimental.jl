```
assemble_basismatrix(
    mesh::Mesh;
    qdim::Int64 = 1,
    order::Int64 = 3
) -> SparseMatrixCSC{Float64, Int64}
```

Returns the discrete basis matrix with given local integration order  for all elements of mesh and qdim components.
