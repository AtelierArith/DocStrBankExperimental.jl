```
AffinityPropResult <: ClusteringResult
```

アフィニティ伝播クラスタリングの出力 ([`affinityprop`](@ref))。

# フィールド

  * `exemplars::Vector{Int}`: *exemplars*（クラスタ中心）のインデックス
  * `assignments::Vector{Int}`: 各データポイントのクラスタ割り当て
  * `iterations::Int`: 実行された反復の数
  * `converged::Bool`: 収束したかどうか
