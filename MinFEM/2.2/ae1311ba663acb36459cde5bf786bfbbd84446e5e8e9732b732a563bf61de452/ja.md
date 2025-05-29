```
assemble_derivativematrix(mesh::Mesh; qdim::Int64=1) -> SparseMatrixCSC{Float64, Int64}
```

メッシュのすべての要素とqdim成分に対する離散微分行列を返します。
