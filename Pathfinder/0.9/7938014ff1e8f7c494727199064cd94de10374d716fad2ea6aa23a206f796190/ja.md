```
PathfinderResult
```

単一路径パスファインダーの結果を格納するコンテナ。

# フィールド

  * `input`: ユーザー提供の入力オブジェクト、例えば LogDensityProblem、`optim_fun`、`optim_prob`、または他のオブジェクト。
  * `optimizer`: 対数密度を最大化するために使用された最適化手法
  * `rng`: サンプリングに使用された擬似乱数生成器
  * `optim_prob::`[`SciMLBase.OptimizationProblem`](@extref): 最適化に使用される最適化問題
  * `logp`: 対数密度関数
  * `fit_distribution::`[`Distributions.MvNormal`](@extref): ELBOを最大化する多変量正規分布
  * `draws::AbstractMatrix{<:Real}`: サイズ `(dim, ndraws)` の多変量正規からのサンプル
  * `fit_distribution_transformed`: ユーザーが提供したターゲット分布と同じ空間に変換された `fit_distribution`。これは、他のパッケージと統合する際にのみ `fit_distribution` と異なり、その型は `input` の型に依存します。
  * `draws_transformed`: `fit_distribution_transformed` からのサンプルとなるように変換された `draws`。
  * `fit_iteration::Int`: ELBO推定が最大化されたイテレーション
  * `num_tries::Int`: パスファインダーが成功するまでの試行回数
  * `optim_solution::`[`SciMLBase.OptimizationSolution`](@extref): 最適化の解オブジェクト。
  * `optim_trace::Pathfinder.OptimizationTrace`: ポイント、対数密度、および勾配の最適化トレースのコンテナ。最初のポイントは初期点です。
  * `fit_distributions::AbstractVector{Distributions.MvNormal}`: `optim_trace` の各ポイントに対する多変量正規分布、ここで `fit_distributions[fit_iteration + 1] == fit_distribution`
  * `elbo_estimates::AbstractVector{<:Pathfinder.ELBOEstimate}`: `fit_distributions` の最初の分布を除くすべてのELBO推定。
  * `num_bfgs_updates_rejected::Int`: 再構成された逆ヘッセ行列へのBFGS更新が拒否された回数、逆ヘッセ行列を正定値に保つため。

# 戻り値

  * [`PathfinderResult`](@ref)
