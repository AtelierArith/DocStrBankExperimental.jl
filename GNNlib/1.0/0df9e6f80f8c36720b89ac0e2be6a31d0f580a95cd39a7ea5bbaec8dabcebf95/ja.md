```
aggregate_neighbors(g, aggr, m)
```

グラフ `g`、エッジ特徴 `m`、および集約演算子 `aggr`（例：`+, min, max, mean`）が与えられると、新しいノード特徴を返します。

$$
\mathbf{x}_i = \square_{j \in \mathcal{N}(i)} \mathbf{m}_{j\to i}
$$

近隣集約は、[`apply_edges`](@ref) の後に続く [`propagate`](@ref) の第二ステップです。
