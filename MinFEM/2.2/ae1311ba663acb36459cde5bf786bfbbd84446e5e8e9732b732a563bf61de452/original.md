```
assemble_derivativematrix(mesh::Mesh; qdim::Int64=1) -> SparseMatrixCSC{Float64, Int64}
```

Returns the discrete derivative matrix for all elements of mesh and qdim components.
