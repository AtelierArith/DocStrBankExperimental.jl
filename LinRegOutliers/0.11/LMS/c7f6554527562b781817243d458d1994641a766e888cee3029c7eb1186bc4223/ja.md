```
lms(setting; iters = nothing, crit = 2.5)
```

ランダムサンプリングを用いた最小中央値二乗回帰推定量を実行します。

# 引数

  * `setting::RegressionSetting`: 回帰設定オブジェクト。
  * `iters::Int`: ランダムサンプルの数。
  * `crit::Float64`: 標準化残差のための臨界値。

# 説明

LMS（最小中央値二乗）推定量は、50%のブレイクダウン特性を持つ非常にロバストな手法です。このアルゴリズムは、(h)番目の順序の二乗残差を最小化する回帰係数を探索します。ここで、hはInt(floor((n + 1.0) / 2.0))です。

# 出力

  * `["stdres"]`: 標準化残差の配列
  * `["S"]`: 回帰の標準誤差
  * `["outliers"]`: 外れ値のインデックスの配列
  * `["objective"]`: LMS目的値
  * `["betas"]`: 推定された回帰係数
  * `["crit"]`: 閾値。

# 例

```julia-repl
julia> reg = createRegressionSetting(@formula(calls ~ year), phones);

julia> lms(reg)
Dict{Any,Any} with 6 entries:
  "stdres"    => [2.28328, 1.55551, 0.573308, 0.608843, 0.220321, -0.168202, -0.471913, -0.860435, -0.31603, -0.110871  …  85.7265, 88.9849, 103.269, 116.705, 135.229, 159.69,…
  "S"         => 1.17908
  "outliers"  => [14, 15, 16, 17, 18, 19, 20, 21]
  "objective" => 0.515348
  "betas"      => [-56.1972, 1.1581]
  "crit"      => 2.5
```

# 参考文献

Rousseeuw, Peter J. "Least median of squares regression." Journal of the American  statistical association 79.388 (1984): 871-880.
