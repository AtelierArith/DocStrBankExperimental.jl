```
ChisqFriedmanTest(x_1, x_2, ..., x_k; kwargs...)
ChisqFriedmanTest(X; kwargs...)
```

`k` の処置のセットに対して `n` 回の繰り返し観測がすべての処置で同じ分布を持つという帰無仮説を検定します。これらの観測は、各 `n` の観測を持つ `k` のベクトル `x_i` に配置されるか、または `(n, k)` 形状の行列 `X` に配置されます。

このバージョンの `FriedmanTest` は χ² 分布の統計量を使用します。

# キーワード引数

  * `maximize_outcome=false` は、ランクが結果の最大化または最小化を表すかどうかを指定します。
