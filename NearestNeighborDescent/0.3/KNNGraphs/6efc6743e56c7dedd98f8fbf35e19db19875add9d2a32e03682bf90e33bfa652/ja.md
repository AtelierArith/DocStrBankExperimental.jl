```
HeapKNNGraph(data, metric, indices, distances)
```

`indices` と `distances` の `KxN` 行列から HeapKNNGraph を作成します。ここで、`indices[i, v]` と `distances[i, v]` はノード `v` の `i` 番目の候補近傍へのインデックスと距離です。`indices` の各列には重複するエントリがあってはなりませんが、距離によってソートされている必要はありません。
