```
has_isolated_nodes(g::GNNGraph; dir=:out)
```

グラフ `g` に出次数（`dir=:out` の場合）または入次数（`dir = :in` の場合）がゼロのノードが含まれている場合は true を返します。
