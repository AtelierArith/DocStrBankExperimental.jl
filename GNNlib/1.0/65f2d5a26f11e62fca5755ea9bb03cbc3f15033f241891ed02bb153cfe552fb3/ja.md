```
reduce_nodes(aggr, g, x)
```

バッチグラフ `g` に対して、ノード特徴 `x` のグラフ単位の集約を返します。集約演算子 `aggr` は `+`、`mean`、`max`、または `min` であることができます。返される配列の最後の次元は `g.num_graphs` になります。

関連情報: [`reduce_edges`](@ref).
