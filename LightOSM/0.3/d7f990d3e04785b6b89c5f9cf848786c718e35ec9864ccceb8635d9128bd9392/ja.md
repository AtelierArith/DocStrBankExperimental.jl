```
shortest_path([PathAlgorithm,]
              g::OSMGraph,
              origin::Union{Integer,Node},
              destination::Union{Integer,Node},
              [weights::AbstractMatrix=g.weights;
              cost_adjustment::Function=(u, v, parents) -> 0.0),
              max_distance::W=typemax(W)]
```

2つのOpenStreetMapノードID間の最短経路を計算します。

# 引数

  * `PathAlgorithm` (オプション): 経路探索アルゴリズム、可能な値は次の通りです：

      * `Dijkstra`: `DijkstraVector`と同じです。これがデフォルトのアルゴリズムです。
      * `DijkstraVector`: `Vector`実装を使用したダイクストラアルゴリズム。小さなグラフや長い経路に対して高速です。
      * `DijkstraDict`: `Dict`実装を使用したダイクストラアルゴリズム。大きなグラフや短い経路に対して高速です。
      * `AStar`: `AStarVector`と同じです。
      * `AStarVector`: `Vector`実装を使用したA*アルゴリズム。小さなグラフや長い経路に対して高速です。
      * `AStarDict`: `Dict`実装を使用したA*アルゴリズム。大きなグラフや短い経路に対して高速です。
  * `g::OSMGraph{U,T,W}`: グラフコンテナ。
  * `origin::Union{Integer,Node}`: 出発点のOpenStreetMapノードまたはノードID。
  * `destination::Union{Integer,Node},`: 目的地のOpenStreetMapノードまたはノードID。
  * `weights`: ノード間のエッジの重みのオプションの行列、デフォルトは`g.weights`です。`AStar`に設定されたカスタム重み行列を使用する場合は、正しいヒューリスティックが使用されていることを確認してください。
  * `cost_adjustment::Function=(u,v,parents) -> 0.0`: 各頂点のペア`u`と`v`間のコストを調整するための関数を渡すオプション。通常、コストは`u`と`v`間の重みだけですが、`cost_adjustment`は3つの引数`u`、`v`、`parents`を受け取り、デフォルトの重みに加算コストを適用します。デフォルトでは調整はありません。ターン制限を考慮するには`restriction_cost_adjustment`を使用します。
  * `heuristic::Function=distance_heuristic(g)`: `AStar`アルゴリズム専用のカスタムヒューリスティックを使用します。デフォルトは`h(u, v) -> haversine(u, v)`という関数で、現在のノード`u`と隣接ノード`v`間のハーバーサイン距離を返します。`g.weight_type`が`:time`または`:lane_efficiency`の場合は、代わりに`time_heuristic(g)`を使用します。

# 戻り値

  * `Union{Nothing,Vector{T}}`: 最短経路を構成するOpenStreetMapノードIDの配列。
