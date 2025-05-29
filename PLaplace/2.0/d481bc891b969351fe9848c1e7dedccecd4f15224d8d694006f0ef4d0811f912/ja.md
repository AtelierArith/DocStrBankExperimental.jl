```
compute_prolongation_zero(
    g::AbstractVector{Float64},
    mesh::Mesh;
    qdim::Int64 = 1
) -> AbstractVector{Float64}
```

gを全領域にわたって各ノードでゼロにより離散的に延長します。

境界条件gを全領域にわたって各ノードでゼロにより離散的に延長します。

# 必須引数

  * `g::AbstractVector{Float64}`: 離散的に評価された境界条件。
  * `mesh::Mesh`: 領域のメッシュ。

# キーワード引数

  * `qdim::Int64 = 1`: f, h, および gの成分数。
