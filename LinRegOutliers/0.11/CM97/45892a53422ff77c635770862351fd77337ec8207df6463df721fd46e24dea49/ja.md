```
cm97(setting; maxiter = 1000)
```

与えられた回帰設定に対して、ChatterjeeとMächler（1997）のアルゴリズムを実行します。

# 引数

  * `setting::RegressionSetting`: フォーミュラとデータセットを持つRegressionSettingオブジェクト。

# 説明

このアルゴリズムは、ロバスト回帰係数を取得するために反復加重最小二乗推定を実行します。

# 出力

  * `["betas"]`: ロバスト回帰係数
  * `["iterations"]`: 実行された反復の数
  * `["converged"]`: アルゴリズムが収束した場合はtrue、そうでない場合はfalse。

# 例

```julia-repl
julia> myreg = createRegressionSetting(@formula(stackloss ~ airflow + watertemp + acidcond), stackloss)
julia> result = cm97(myreg)
Dict{String,Any} with 3 entries:
  "betas"      => [-37.0007, 0.839285, 0.632333, -0.113208]
  "iterations" => 22
  "converged"  => true
```

# 参考文献

Chatterjee, Samprit, and Martin Mächler. "Robust regression: A weighted least squares approach."  Communications in Statistics-Theory and Methods 26.6 (1997): 1381-1394.
