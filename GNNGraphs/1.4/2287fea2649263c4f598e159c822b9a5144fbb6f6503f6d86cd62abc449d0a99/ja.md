```
add_nodes(g::GNNGraph, n; [ndata])
```

グラフ `g` に `n` 個の新しいノードを追加します。新しいグラフでは、これらのノードは `g.num_nodes + 1` から `g.num_nodes + n` までのインデックスを持ちます。
