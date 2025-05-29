```
Graphs.outneighbors(g::SimpleWeightedDiGraph, v)
```

頂点 `v` の出辺のベクトルを返します。

!!! tip "パフォーマンス"
    この関数は、有向重み付きグラフに対して `inneighbors` よりも効率的です。

