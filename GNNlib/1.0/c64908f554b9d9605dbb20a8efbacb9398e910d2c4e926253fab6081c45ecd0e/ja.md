```
broadcast_nodes(g, x)
```

グラフ全体に対して、サイズ `(*, g.num_graphs)` の配列 `x` をサイズ `(*, g.num_nodes)` にブロードキャストします。
