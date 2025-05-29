```
nearest_node(g::OSMGraph, point::GeoLocation)
nearest_node(g::OSMGraph, points::Vector{GeoLocation})
nearest_node(g::OSMGraph, point::AbstractVector{<:AbstractFloat})
nearest_node(g::OSMGraph, points::AbstractVector{<:AbstractVector{<:AbstractFloat}})
```

指定されたポイント（`GeoLocation`または緯度経度座標のセット）または`NearestNeighbors.jl`のKDTreeを使用してポイントの`Vector`から最も近いノードを見つけます。

# 引数

  * `g::OSMGraph`: グラフコンテナ。
  * `point`/`points`: `GeoLocation`としての単一ポイントまたは`[lat, lon, alt]`、またはそのようなポイントの`Vector`

# 戻り値

  * 各ポイントからの隣接ノードと直線ユークリッド距離のタプル`([neighbours...], [dists...])`。タプルの要素は、ポイントの`Vector`が入力された場合は`Vector`であり、単一ポイントが入力された場合は数値です。
