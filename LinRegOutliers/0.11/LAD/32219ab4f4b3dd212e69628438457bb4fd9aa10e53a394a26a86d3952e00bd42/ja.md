```
lad(setting; exact = true)
```

与えられた回帰設定に対して最小絶対偏差回帰を実行します。

# 引数

  * `setting::RegressionSetting`: フォーミュラとデータセットを持つRegressionSettingオブジェクト。
  * `exact::Bool`: trueの場合、正確なLAD回帰を使用します。falseの場合、GAを使用してLAD回帰パラメータを推定します。デフォルトはtrueです。

# 説明

LAD推定量は、絶対残差の合計を最小化する回帰パラメータの推定値を探索します。最適化問題は次のようになります。

Min z = u1(-) + u1(+) + u2(-) + u2(+) + .... + un(-) + un(+) 制約条件:     y*1 - beta0 - beta1 * x*2 + u1(-) - u1(+) = 0     y*2 - beta0 - beta1 * x*2 + u2(-) - u2(+) = 0     .     .     .     y*n - beta0 - beta1 * x*n + un(-) - un(+) = 0 ここで      ui(-), ui(+) >= 0     i = 1, 2, ..., n      beta0, beta1 in R      n : 観測数 

# 出力

  * `["betas"]`: 推定された回帰係数
  * `["residuals"]`: 回帰残差
  * `["model"]`: 線形計画モデル

# 例

```julia-repl
julia> reg0001 = createRegressionSetting(@formula(calls ~ year), phones);
julia> lad(reg0001)
Dict{Any,Any} with 2 entries:
  "betas"     => [-57.3269, 1.19155]
  "residuals" => [2.14958, 1.25803, 0.0664872, 0.0749413, -0.416605, -0.90815, -1.2997, -1.79124,…

```
