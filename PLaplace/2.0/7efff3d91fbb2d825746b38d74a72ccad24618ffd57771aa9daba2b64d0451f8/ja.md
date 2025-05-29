```
assemble_derivativetensor(
    mesh::Mesh;
    qdim::Int64 = 1
) -> Dict{Tuple{Int64, Int64}, SparseArrays.SparseMatrixCSC{Float64, Int64}}
```

メッシュのすべての要素に対する離散導関数テンソルと、関数の成分数 qdim を返します。各キーのタプル (j,r) は、方向 x_j における成分 r の導関数行列を表します。
