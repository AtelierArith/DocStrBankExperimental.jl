```
ks89(setting; alpha = 0.05)
```

与えられた回帰設定に対してKianifard & Swallow (1989)アルゴリズムを実行します。

# 引数

  * `setting::RegressionSetting`: フォーミュラとデータセットを持つRegressionSettingオブジェクト。
  * `alpha::Float64`: 帰無仮説を棄却する確率のオプション引数。

# 説明

このアルゴリズムは、クリーンな観測値のサブセットから始まります。この初期セットは、再帰的残差を使用して拡大されます。計算された統計量が閾値を超えると、アルゴリズムは終了します。

# 出力

  * `["outliers]`: 外れ値のインデックスの配列。
  * `["betas"]`: 回帰係数のベクトル。

# 例

```julia-repl
julia> reg0001 = createRegressionSetting(@formula(stackloss ~ airflow + watertemp + acidcond), stackloss)
julia> ks89(reg0001)
Dict{String, Vector} with 2 entries:
  "betas"    => [-42.4531, 0.956605, 0.555571, -0.108766]
  "outliers" => [4, 21]
```

# 参考文献

Kianifard, Farid, and William H. Swallow. "Using recursive residuals, calculated on adaptively-ordered observations, to identify outliers in linear regression." Biometrics (1989): 571-585.
