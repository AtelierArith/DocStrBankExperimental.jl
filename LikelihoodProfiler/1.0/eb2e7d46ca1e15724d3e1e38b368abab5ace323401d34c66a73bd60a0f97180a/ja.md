```
PLProblem{T,probType,P,PF,PR}
```

プロファイル尤度問題を定義します。

## プロファイル尤度問題の数学的仕様：

プロファイル尤度問題は以下によって定義されます。

  * 目的関数（通常は負の対数尤度関数）が `optprob::OptimizationProblem` 内にラップされています。詳細については [Optimization.jl docs](https://docs.sciml.ai/Optimization/stable/API/optimization_problem/) を参照してください。
  * 目的関数を最小化するパラメータ `optpars` の最適値のセット。

### コンストラクタ

```julia
PLProblem(optprob, optpars, profile_range = tuple.(optprob.lb, optprob.ub); 
  conf_level = 0.95, df = 1, threshold = chi2_quantile(conf_level, df))
```

### 引数

  * `optprob`: 解決すべき `OptimizationProblem`。
  * `optpars`: パラメータの初期（最適）値。
  * `profile_range`: プロファイル尤度が計算される範囲。デフォルトは `tuple.(lb,ub)` の `OptimizationProblem` です。

### キーワード引数

  * `conf_level`: プロファイル尤度の信頼レベル。デフォルトは `0.95`。
  * `df`: プロファイル尤度の自由度。デフォルトは `1`。
  * `threshold`: プロファイル尤度の閾値。信頼区間の端点推定が必要ない場合は `Inf` に設定できます。デフォルトは `chi2_quantile(conf_level, df)` です。
