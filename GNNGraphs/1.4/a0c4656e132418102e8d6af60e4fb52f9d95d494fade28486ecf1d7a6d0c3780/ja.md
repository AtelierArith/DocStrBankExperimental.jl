```
graph_indicator(g::GNNHeteroGraph, [node_t])
```

グラフ内の各ノードのグラフメンバーシップ（`1` から `g.num_graphs` までの整数）を各ノードタイプごとに含むベクトルの辞書を返します。`node_t` が提供されている場合は、タイプ `node_t` の各ノードのグラフメンバーシップを返します。

詳細は [`batch`](@ref) を参照してください。
