```
assemble_massmatrix_boundary(
    mesh::Mesh; 
    boundaryElements::Set{Int64} = Set{Int64}(), 
    qdim::Int64 = 1,
    order::Int64 = 1
) -> SparseMatrixCSC{Float64, Int64}
```

Returns the mass matrix with given local integration order  for all or specified boundary elements of mesh and image dimension qdim components.
