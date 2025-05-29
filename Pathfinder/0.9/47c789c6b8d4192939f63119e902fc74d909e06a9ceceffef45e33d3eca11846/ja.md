```
MultiPathfinderResult
```

マルチパスファインダーの結果のコンテナ。

# フィールド

  * `input`: ユーザー提供の入力オブジェクト、例えば `logp`、`(logp, ∇logp)`、`optim_fun`、`optim_prob`、または他のオブジェクト。
  * `optimizer`: 対数密度を最大化するために使用された最適化手法
  * `rng`: サンプリングに使用された擬似乱数生成器
  * `optim_prob::`[`SciMLBase.OptimizationProblem`](@extref): 最適化に使用された最適化問題
  * `logp`: 対数密度関数
  * `fit_distribution::`[`Distributions.MixtureModel`](@extref): 各実行からのELBO最大化多変量正規分布の均等重み付き混合。
  * `draws::AbstractMatrix{<:Real}`: `fit_distribution`からのサンプルで、サイズは`(dim, ndraws)`、ターゲット分布に近づくように重要度再サンプリングを使用して再サンプリングされる可能性があります。
  * `draw_component_ids::Vector{Int}`: `draws`内の各サンプルのコンポーネントID。
  * `fit_distribution_transformed`: ユーザー提供のターゲット分布と同じ空間に変換された`fit_distribution`。これは、他のパッケージと統合する際にのみ`fit_distribution`と異なり、その型は`input`の型に依存します。
  * `draws_transformed`: `fit_distribution_transformed`からのサンプルとなるように変換された`draws`。
  * `pathfinder_results::Vector{<:`[`PathfinderResult`](@ref)`}`: 各単一路径パスファインダー実行の結果。
  * `psis_result::Union{Nothing,<:`[`PSIS.PSISResult`](@extref)`}`: 重要度再サンプリングが使用された場合、パレート平滑化された重要度再サンプリングの結果。`psis_result.pareto_shape`は、`draws`がターゲット分布からの推定を計算するために使用できるかどうかを診断します。
