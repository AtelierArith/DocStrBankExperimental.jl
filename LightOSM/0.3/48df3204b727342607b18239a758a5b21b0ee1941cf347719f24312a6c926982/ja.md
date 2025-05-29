```
path_from_parents(parents::P, goal::V) where {P <: Union{<:AbstractVector{<:U}, <:AbstractDict{<:U, <:U}}} where {U <: Integer, V <: Integer}
```

与えられたソースのダイクストラ親から最短経路を抽出します。

# 引数

  * `parents::Union{<:AbstractVector{<:U}, <:AbstractDict{<:U, <:U}}`: ダイクストラ親状態のマッピング。
  * `goal::V`: 目標頂点。

# 戻り値

  * `Union{Nothing,Vector{U}}`: `goal` への最短経路を表す配列頂点。
