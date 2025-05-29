```
struct TransitionMatrix{S, C}
```

[`Stochasticity`](@ref) `S` と [`Connectivity`](@ref) `C` を持つ遷移確率行列。

### フィールド

  * `P`: 遷移確率 `Matrix` 自体。
  * `stochasticity`: `S`
  * `connectivity`: `C`

### コンストラクタ

```
TransitionMatrix(P_size; n_zeros = 0, normalize = true, seed = 1234)
```

ランダムに生成された遷移行列を構築します。

引数 

  * `P_size`: 行数（== 列数）の数。

オプション引数 

  * `n_zeros`: この数のゼロが行列にランダムに配置されます。これにより行列の行がすべてゼロになる場合、その行にランダムに `1` が配置されます。
  * `normalize`: 結果の行列の行の合計を正規化するかどうか。
  * `seed`: 再現可能なランダム性のためのシード。

# 

```
TransitionMatrix(P)
```

行列 `P` から `TransitionMatrix` を構築します。`P` の特性は自動的に推測されます。

引数 

  * `P`: 遷移行列。
