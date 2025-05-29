```
double_cycle([rng], [T], dims...; 
    cycle_weight=0.1, second_cycle_weight=0.1,
    return_sparse=false)
```

ダブルサイクルリザーバを作成します [^fu2023].

# 引数

  * `rng`: ランダム数生成器。デフォルトはWeightInitializersの`Utils.default_rng()`です。
  * `T`: リザーバ行列の要素の型。デフォルトは`Float32`です。
  * `dims`: リザーバ行列の次元。

# キーワード引数

  * `cycle_weight`: リザーバ行列の上部サイクル接続の重み。デフォルトは0.1です。
  * `second_cycle_weight`: リザーバ行列の下部サイクル接続の重み。デフォルトは0.1です。
  * `return_sparse`: `sparse`行列を返すためのフラグ。デフォルトは`false`です。

# 例

```jldoctest
julia> reservoir_matrix = double_cycle(5, 5; cycle_weight=0.1, second_cycle_weight=0.3)
5×5 Matrix{Float32}:
 0.0  0.3  0.0  0.0  0.3
 0.1  0.0  0.3  0.0  0.0
 0.0  0.1  0.0  0.3  0.0
 0.0  0.0  0.1  0.0  0.3
 0.1  0.0  0.0  0.1  0.0
```

[^fu2023]: Fu, Jun, et al. "A double-cycle echo state network topology for time series prediction." Chaos: An Interdisciplinary Journal of Nonlinear Science 33.9 (2023).
