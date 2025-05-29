```
KmedoidsResult{T} <: ClusteringResult
```

[`kmedoids`](@ref) 関数の出力。

# フィールド

  * `medoids::Vector{Int}`: $k$ メドイドのインデックス
  * `assignments::Vector{Int}`: ポイントが割り当てられたクラスタのインデックス。したがって、`medoids[assignments[i]]` は $i$-番目のポイントのメドイドのインデックスです。
  * `costs::Vector{T}`: 割り当てコスト。すなわち、`costs[i]` は $i$-番目のポイントをそのメドイドに割り当てるコストです。
  * `counts::Vector{Int}`: クラスタのサイズ
  * `totalcost::Float64`: 総割り当てコスト（`costs` の合計）
  * `iterations::Int`: 実行されたアルゴリズムの反復回数
  * `converged::Bool`: 手続きが収束したかどうか
