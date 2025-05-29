```
assemble_dirichletprojection(
    ncoeffs::Int64,
    DI::Set{Int64};
    qdim::Int64 = 1
) -> SparseMatrixCSC{Float64, Int64}
```

Returns the projection matrix onto the Dirichlet nodes  where the input ncoeffs is understood as qdim*nnodes.
