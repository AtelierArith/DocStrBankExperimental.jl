```
assemble_derivativematrix_boundary(
    mesh::Mesh; 
    boundaryElements::Set{Int64} = Set{Int64}(), 
    qdim::Int64 = 1
) -> SparseMatrixCSC{Float64, Int64}
```

メッシュのすべてまたは指定された境界要素とqdim成分のための離散導関数行列を返します。

実装は、対応する完全要素の導関数テンソルと、線形要素に対して要素上で勾配が一定であるという事実に基づいています。
