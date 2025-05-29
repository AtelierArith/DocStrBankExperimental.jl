```
quantileregression(setting; tau = 0.5)
```

与えられた回帰設定（重回帰）に対して分位回帰を実行します。

# 引数

  * `setting::RegressionSetting`: フォーミュラとデータセットを持つRegressionSettingオブジェクト。
  * `tau::Float64`: 分位レベル。デフォルトは0.5。

# 説明

分位回帰推定量は、次の条件を満たす回帰パラメータの推定値を最小化することを目指します。

Min z = (1 - tau) (u1(-) + u2(-) + ... + un(-)) + tau (u1(+) + u2(+) + ... + un(+)) 制約条件:     y*1 - beta0 - beta1 * x*2 + u1(-) - u1(+) = 0     y*2 - beta0 - beta1 * x*2 + u2(-) - u2(+) = 0     .     .     .     y*n - beta0 - beta1 * x*n + un(-) - un(+) = 0 ここで      ui(-), ui(+) >= 0     i = 1, 2, ..., n      beta0, beta1 は R に属する      n : 観測数      モデルは y = beta1 + beta2 * x + u 

# 出力

  * `["betas"]`: 推定された回帰係数
  * `["residuals"]`: 回帰残差
  * `["model"]`: 線形計画モデル

# 例

```julia-repl
julia> reg0001 = createRegressionSetting(@formula(calls ~ year), phones);
julia> quantileregression(reg0001)
```
