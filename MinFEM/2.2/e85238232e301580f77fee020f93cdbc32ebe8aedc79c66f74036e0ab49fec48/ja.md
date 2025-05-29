```
assemble_dirichletprojection(
    ncoeffs::Int64,
    DI::Set{Int64};
    qdim::Int64 = 1
) -> SparseMatrixCSC{Float64, Int64}
```

ディリクレノードへの射影行列を返します。入力のncoeffsはqdim*nnodesとして理解されます。
