```
nearest_nodes(g::OSMGraph, point::GeoLocation, n_neighbours::Integer=1)
nearest_nodes(g::OSMGraph, points::AbstractVector{GeoLocation}, n_neighbours::Integer=1)
nearest_nodes(g::OSMGraph, point::AbstractVector{<:AbstractFloat}, n_neighbours::Integer=1)
nearest_nodes(g::OSMGraph, points::AbstractVector{<:AbstractVector{<:AbstractFloat}}, n_neighbours::Integer=1)
```

ポイントまたはポイントの`Vector`から最近のノードを`NearestNeighbors.jl`のKDTreeを使用して見つけます。

# 引数

  * `g::OSMGraph`: グラフコンテナ。
  * `point`/`points`: `GeoLocation`としての単一ポイントまたは`[lat, lon, alt]`、またはそのようなポイントの`Vector`
  * `n_neighbours::Integer`: 各ポイントに対してクエリする隣接ノードの数。

# 戻り値

  * 各ポイントからの隣接ノードと直線ユークリッド距離のタプル`([[neighbours]...], [[dists]...])`。タプルの要素は、ポイントの`Vector`が入力された場合は`Vector{Vector}`、単一ポイントが入力された場合は`Vector`です。
