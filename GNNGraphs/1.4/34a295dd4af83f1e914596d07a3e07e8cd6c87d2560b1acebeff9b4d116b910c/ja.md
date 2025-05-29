```
remove_self_loops(g::GNNGraph)
```

自己ループ（ノードから自身へのエッジ）を削除した `g` から構築されたグラフを返します。

[`add_self_loops`](@ref) および [`remove_multi_edges`](@ref) も参照してください。
