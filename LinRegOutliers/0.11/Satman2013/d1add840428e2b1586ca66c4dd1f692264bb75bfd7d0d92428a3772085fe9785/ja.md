```
satman2013(setting)
```

与えられた回帰設定に対してSatman (2013)アルゴリズムを実行します。

# 引数

  * `setting::RegressionSetting`: フォーミュラとデータセットを持つRegressionSettingオブジェクト。

# 説明

このアルゴリズムは、ロバストなマハラノビス距離を計算するための高速で堅牢な共分散行列を構築します。これらの距離は、後の加重最小二乗推定で使用するための重みを構築するために使用されます。最後の段階では、前の段階で見つかった基本的なサブセットに対してCステップが繰り返されます。

# 出力

  * `["outliers"]`: 外れ値のインデックスの配列。
  * `["betas"]`: 推定された回帰係数の配列。
  * `["residuals"]`: 残差の配列。

# 例

```julia-repl
julia> eg0001 = createRegressionSetting(@formula(y ~ x1 + x2 + x3), hbk);
julia> satman2013(reg0001)
Dict{Any,Any} with 1 entry:
  "outliers" => [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 47]
  "betas" => ...
  "residuals" => ...
```

# 参考文献

Satman, Mehmet Hakan. "A new algorithm for detecting outliers in linear regression."  International Journal of statistics and Probability 2.3 (2013): 101.
