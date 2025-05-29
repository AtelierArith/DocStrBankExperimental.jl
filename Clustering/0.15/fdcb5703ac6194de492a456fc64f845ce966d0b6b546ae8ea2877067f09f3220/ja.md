```
DbscanCluster
```

DBSCANクラスタは、[`dbscan`](@ref)関数によって返される[`DbscanResult`](@ref)の一部です。

## フィールド

  * `size::Int`: クラスタ内のポイント数（コア + バウンダリ）
  * `core_indices::Vector{Int}`: クラスタの*コア*、すなわち*シード*のポイントのインデックス（クラスタ内に少なくとも`min_neighbors`の隣接点を持つ）
  * `boundary_indices::Vector{Int}`: *コア*の外にあるクラスタポイントのインデックス
