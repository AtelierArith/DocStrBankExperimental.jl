```
nearest_node(g::OSMGraph, node::Node)
nearest_node(g::OSMGraph, nodes::Vector{<:Node})
nearest_node(g::OSMGraph, node_ids::AbstractVector{<:Integer})
nearest_node(g::OSMGraph, node_id::Integer)
```

ノード（`Node`オブジェクトまたはノードIDで指定）またはノードの`Vector`から最も近いノードを`NearestNeighbors.jl`のKDTreeを使用して見つけます。元のノード自体は結果に含まれません。

# 引数

  * `g::OSMGraph`: グラフコンテナ。
  * `node`/`nodes`/`node_id`/`node_ids`: `Node`オブジェクトまたはIDで指定された単一ノードまたはノードの`Vector`。

# 戻り値

  * 隣接ノードと各ノードからの直線ユークリッド距離のタプル`([neighbours...], [dists...])`。タプルの要素は、ノードの`Vector`が入力された場合は`Vector`、単一のポイントが入力された場合は数値です。
