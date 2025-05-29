```
FriedmanTest(x_1, x_2, ..., x_k; kwargs...) = FDistFriedmanTest(x_1, x_2, ..., x_k; kwargs...)
FriedmanTest(X; kwargs...) = FDistFriedmanTest(X; kwargs...)
```

`n` 回の繰り返し観測が `k` 種類の処置のセット全体で同じ分布を持つという帰無仮説を検定します。これらの観測は、各 `n` 回の観測を持つ `k` 個のベクトル `x_i` に配置されるか、または `(n, k)` 形状の行列 `X` に配置されます。

このテストのデフォルトバージョンである `FDistFriedmanTest` は、F分布に従う統計量を使用します。

**関連情報:** `FDistFriedmanTest`, `ChisqFriedmanTest`

# キーワード引数

  * `maximize_outcome=false` は、ランクが結果の最大化または最小化を表すかどうかを指定します。
