```
outedgevals(g::AbstractValGraph, v [, key])
```

`v` から隣接ノードへの出力エッジのエッジ値のイテレータを返します。

`g` に複数のエッジ値がある場合、キーを省略することはできません。隣接ノードの順序は `outneighbors(g, v)` と同じです。
