```
assemble_derivativetensor_boundary(
    mesh::Mesh,
    BoundaryElements::Set{Int64}; 
    qdim::Int64 = 1
) -> Dict{Tuple{Int64, Int64}, SparseArrays.SparseMatrixCSC{Float64, Int64}}
```

メッシュのすべてまたは指定された境界要素の離散導関数テンソルと成分数 qdim を返します。各キーのタプル (j,r) は、方向 x_j における成分 r の導関数行列を表します。対応する完全要素の導関数テンソルと、要素上で勾配が一定であるという事実に基づくワークアラウンドです。
