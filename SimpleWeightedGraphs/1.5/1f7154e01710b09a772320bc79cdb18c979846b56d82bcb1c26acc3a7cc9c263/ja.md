```
Graphs.inneighbors(g::SimpleWeightedDiGraph, v)
```

頂点 `v` の内側の隣接点のベクトルを返します。

!!! tip "パフォーマンス"
    この関数は、有向重み付きグラフに対して `inneighbors` よりも効率が悪いです（新しいベクトルを割り当てます）。

