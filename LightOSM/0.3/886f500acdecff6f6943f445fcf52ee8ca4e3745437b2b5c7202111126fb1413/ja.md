```
path_from_parents(parents::P, goal::V, path_length::N) where {P <: Union{<:AbstractVector{<:U}, <:AbstractDict{<:U, <:U}}} where {U <: Integer, V <: Integer, N <: Integer}
```

与えられたソースのダイクストラ親から最短経路を抽出し、`path_length`を提供することで配列の事前割り当てを可能にし、経路を逆転させる必要を回避します。

# 引数

  * `parents::Union{<:AbstractVector{<:U}, <:AbstractDict{<:U, <:U}}`: ダイクストラ親状態のマッピング。
  * `goal::V`: 目標頂点。
  * `path_kength::N`: 戻り経路の既知の長さで、最終経路配列の事前割り当てを可能にします。

# 戻り値

  * `Union{Nothing,Vector{U}}`: `goal`への最短経路を表す配列頂点。
