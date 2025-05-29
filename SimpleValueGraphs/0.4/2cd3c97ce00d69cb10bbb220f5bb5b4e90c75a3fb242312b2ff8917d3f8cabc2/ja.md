```
inedgevals(g::AbstractValGraph, v [, key])
```

隣接ノード `v` からの入ってくるエッジの値のイテレータを返します。

`g` に複数のエッジ値がある場合、キーを省略することはできません。隣接ノードの順序は `inneighbors(g, v)` と同じです。
