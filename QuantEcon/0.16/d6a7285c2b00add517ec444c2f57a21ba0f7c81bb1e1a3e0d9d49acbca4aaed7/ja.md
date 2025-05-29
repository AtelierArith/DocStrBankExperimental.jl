```
random_stochastic_matrix([rng], n[, k])
```

`k` の非ゼロエントリを持つ `n x n` 確率行列をランダムにサンプリングして返します。

# 引数

  * `rng::AbstractRNG=GLOBAL_RNG` : 擬似乱数生成器。
  * `n::Integer` : 状態の数。
  * `k::Integer=n` : 行列の各列における非ゼロエントリの数。指定がない場合は `n` に設定されます。

# 戻り値

  * `p::Array` : 確率行列。

```
