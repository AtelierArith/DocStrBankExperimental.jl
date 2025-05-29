```
nearest_nodes(g::OSMGraph, node_id::DEFAULT_OSM_ID_TYPE, n_neighbours::Integer=1)
nearest_nodes(g::OSMGraph, node_ids::Vector{<:DEFAULT_OSM_ID_TYPE}, n_neighbours::Integer=1)
nearest_nodes(g::OSMGraph, node::Node, n_neighbours::Integer=1)
nearest_nodes(g::OSMGraph, nodes::AbstractVector{<:Node}, n_neighbours::Integer=1)
```

ポイントまたはポイントの`Vector`から最近のノードを`NearestNeighbors.jl`のKDTreeを使用して見つけます。

# 引数

  * `g::OSMGraph`: グラフコンテナ。
  * `node`/`nodes`/`node_id`/`node_ids`: `Node`オブジェクトまたはIDで指定された単一のノードまたはノードの`Vector`。
  * `n_neighbours::Integer`: 各ポイントに対してクエリする隣接ノードの数。

# 戻り値

  * 各ポイントからの隣接ノードと直線ユークリッド距離のタプル`([[neighbours]...], [[dists]...])`。タプルの要素は、ポイントの`Vector`が入力された場合は`Vector{Vector}`、単一のポイントが入力された場合は`Vector`です。
