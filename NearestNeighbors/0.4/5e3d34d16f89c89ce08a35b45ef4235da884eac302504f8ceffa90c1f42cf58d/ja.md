```
knn(tree::NNTree, points, k [, sortres=false]) -> indices, distances
```

`tree`内のデータから`points`に最も近い`k`個の近傍を検索します。`skip`は、返されるべき点をそのインデックスに基づいてスキップするかどうかを決定するためのオプションの述語です。

関連情報: `knn!`, `nn`.
