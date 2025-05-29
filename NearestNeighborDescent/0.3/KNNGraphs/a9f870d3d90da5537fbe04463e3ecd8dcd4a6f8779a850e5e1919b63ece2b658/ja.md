```
knn_matrices(graph) -> indices, distances
```

近似KNNのインデックスと距離を密行列として返します。ここで、indices[j, i]はノードiのj番目の最近傍のインデックス、distances[j, i]はその距離です。
