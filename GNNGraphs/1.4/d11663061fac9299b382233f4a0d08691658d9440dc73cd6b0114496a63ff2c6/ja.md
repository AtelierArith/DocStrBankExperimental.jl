```
graph_indicator(g::GNNGraph; edges=false)
```

グラフ内の各ノードのグラフメンバーシップ（`1` から `g.num_graphs` までの整数）を含むベクトルを返します。`edges=true` の場合は、各エッジのグラフメンバーシップを返します。
