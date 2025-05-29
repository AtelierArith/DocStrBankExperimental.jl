```
dijkstra(distmx::AbstractSparseMatrixCSC, state::DijkstraState, [target]) -> Nothing
```

`distmx`が与えられたとき、`distmx[j, i]`は弧i→jの距離であり、構造的ゼロは弧がないことを意味します。ダイクストラアルゴリズムを終了するか、ターゲットに到達するまで（どちらか早く発生する方）実行します。
