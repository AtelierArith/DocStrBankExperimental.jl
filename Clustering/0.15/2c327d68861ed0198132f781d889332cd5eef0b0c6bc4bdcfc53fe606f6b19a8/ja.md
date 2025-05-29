```
DbscanResult <: ClusteringResult
```

[`dbscan`](@ref) 関数の出力。

## フィールド

  * `clusters::Vector{DbscanCluster}`: クラスタ、長さ *K*
  * `seeds::Vector{Int}`: 各クラスタの *core* の最初のポイントのインデックス、長さ *K*
  * `counts::Vector{Int}`: クラスタサイズ（割り当てられたポイントの数）、長さ *K*
  * `assignments::Vector{Int}`: 各ポイントが割り当てられたクラスタのインデックスのベクター、長さ *N*
