```
NegativeDistanceHack(dist)
```

距離関数をラップしたものの負の値として評価されます。これは実際の距離関数ではなく、類似性を得て、これを使用してこのハックを処理できるインデックス上で最も遠い要素（最も遠い点 / 最も遠いペア）を検索するための単純なハックです（例：`ExhaustiveSearch`、`ParallelExhaustiveSearch`、`SearchGraph`）。
