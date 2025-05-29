```
bd_coef_between(causet, i, j, dim, locality[, max_cardinality]) -> Float64
```

時空原子 `i` に対する時空原子 `j` のベニンカサ-ダウカー係数を返します。2つの原子が関連していない場合や `max_cardinality` を超えた場合は `0` を返します。
