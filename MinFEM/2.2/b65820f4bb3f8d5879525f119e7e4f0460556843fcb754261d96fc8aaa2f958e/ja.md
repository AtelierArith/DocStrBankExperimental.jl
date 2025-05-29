```
assemble_laplacian(
    mesh::Mesh;
    qdim::Int64 = 1
) -> SparseMatrixCSC{Float64, Int64}
```

メッシュのすべての要素とqdim成分のラプラス剛性行列を返します。
