```
shortest_path_from_dijkstra_state(g::OSMGraph, origin::Integer, destination::Integer)
```

事前に計算されたダイクストラ状態から、`origin` から `destination` ノード ID までの最短経路を抽出します。

注意: 原点ノードのダイクストラ状態が事前に計算されていない場合、関数は `UndefRefError: access to undefined reference` を発生させます。

# 引数

  * `g::OSMGraph`: グラフコンテナ。
  * `origin::Integer`: 原点のOpenStreetMapノードまたはノードID。
  * `destination::Integer`: 目的地のOpenStreetMapノードまたはノードID。

# 戻り値

  * `Union{Nothing,Vector{T}}`: 最短経路を構成するOpenStreetMapノードIDの配列。
