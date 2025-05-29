```
grid_dijkstra(g, s)
```

`GridGraph` `g` に対してダイクストラのアルゴリズムを適用し、ソース `s` を持つ `ShortestPathTree` を返します。

内部で `DataStructures.BinaryHeap` を使用し、`DataStructures.PriorityQueue` は使用しません。ForwardDiff と互換性があります。
