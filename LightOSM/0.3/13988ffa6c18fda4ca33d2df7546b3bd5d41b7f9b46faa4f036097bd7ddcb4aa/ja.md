```
weights_from_path(g::OSMGraph{U,T,W}, path::Vector{T}; weights=g.weights)::Vector{W} where {U <: DEFAULT_OSM_INDEX_TYPE,T <: DEFAULT_OSM_ID_TYPE,W <: Real}
```

パスからエッジの重みを抽出します。重み行列は `g.weights` に保存されており、異なる行列が `weights` キーワード引数に渡されない限り、それが使用されます。

# 引数

  * `g::OSMGraph`: グラフコンテナ。
  * `path::Vector{T}`: OpenStreetMapノードIDの配列。
  * `weights=g.weights`: エッジの重みが抽出される行列。デフォルトは `g.weights` です。

# 戻り値

  * `Vector{W}`: エッジの重みの配列、距離はkm、時間は時間単位です。
