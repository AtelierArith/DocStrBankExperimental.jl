```
reduce_nodes(aggr, indicator::AbstractVector, x)
```

グラフインジケータ `indicator` に基づいてノード特徴 `x` のグラフ単位の集約を返します。集約演算子 `aggr` は `+`、`mean`、`max`、または `min` であることができます。

詳細は [`graph_indicator`](@ref) を参照してください。
