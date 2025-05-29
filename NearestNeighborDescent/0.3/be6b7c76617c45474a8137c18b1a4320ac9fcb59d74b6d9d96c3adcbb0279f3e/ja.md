```
search(graph, queries, n_neighbors; max_candidates) -> indices, distances
```

`queries`内のポイントの最近傍を見つけるためにkNN `graph`を検索します。`max_candidates`は候補キューのサイズを制御します（最小`n_neighbors`）；大きな値は速度の代わりに精度を向上させます。
