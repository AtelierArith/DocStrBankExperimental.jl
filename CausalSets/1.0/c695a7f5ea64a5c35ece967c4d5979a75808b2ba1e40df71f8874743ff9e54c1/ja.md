```
cardinality_of(causet, i, j[, max_cardinality]) -> Union{Int64, Nothing}
```

$$
Z(e_i, e_j)
$$

の基数を計算します。$e_i$が$e_j$の過去にない場合は`nothing`を返します。

パラメータ`max_cardinality`が指定されている場合、基数が`max_cardinality`を超えるときは`nothing`を返します。これは最適化の目的で便利です。
