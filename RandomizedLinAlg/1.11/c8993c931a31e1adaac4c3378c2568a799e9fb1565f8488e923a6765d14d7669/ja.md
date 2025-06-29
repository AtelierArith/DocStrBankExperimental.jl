```
rnorm(A, mvps)
```

行列 `A` のノルムに対する確率的上限を計算します。`‖A‖ ≤ α √(2/π) maxᵢ ‖Aωᵢ‖` で、確率 `p=α^(-mvps)` です。

# 引数

  * `A`: ノルムを推定する行列。
  * `mvps::Int`: 計算する行列-ベクトル積の数。

## キーワード

  * `p::Real=0.05`: 上限が失敗する確率。

# 出力

‖A‖ の推定値。

別の推定器については [`rnorms`](@ref) を参照してください。これは、`A` と `A'` の両方で前乗算を使用します。

# 参考文献

Halko2011 の補題 4.1
