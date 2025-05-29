```
SimilarityFromDistance(dist)
```

距離評価 `d` に対して $1/(1 + d)$ として評価されます。これは距離関数ではなく、このハックを処理できるインデックス上で最も遠い要素を検索するための類似性を得るためのハックの一部です（例：`ExhaustiveSearch`、`ParallelExhaustiveSearch`、`SearchGraph`）。
