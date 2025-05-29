```
total_path_weight(g::OSMGraph{U,T,W}, path::Vector{T}; weights=g.weights)::W where {U <: Integer,T <: DEFAULT_OSM_ID_TYPE,W <: Real}
```

パスに沿った合計エッジ重みを抽出します。

# 引数

  * `g::OSMGraph`: グラフコンテナ。
  * `path::Vector{T}`: OpenStreetMapノードIDの配列。
  * `weights=g.weights`: エッジ重みが抽出される行列。デフォルトは`g.weights`です。

# 戻り値

  * `sum::W`: 合計パスエッジ重み、距離はkm、時間は時間単位です。
