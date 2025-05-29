```
estimate_objective([rng,] obj, q, prob; kwargs...)
```

目的関数 `obj` を、変分近似 `q` に関して、対象の確率 `prob` に対して推定します。

# 引数

  * `rng::Random.AbstractRNG`: 擬似乱数生成器。
  * `obj::AbstractVariationalObjective`: 変分目的関数。
  * `prob`: `LogDensityProblem` インターフェースを実装する対象の対数結合尤度。
  * `q`: 変分近似。

# キーワード引数

目的に応じて、追加のキーワード引数が適用される場合があります。詳細については、それぞれの変分目的関数のドキュメントを参照してください。

# 戻り値

  * `obj_est`: 目的関数の値の推定。
