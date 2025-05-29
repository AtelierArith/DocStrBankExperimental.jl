```julia
solve(
    prob::HighDimPDE.ParabolicPDEProblem,
    alg::HighDimPDE.DeepBSDE;
    dt,
    abstol,
    verbose,
    maxiters,
    save_everystep,
    trajectories,
    ensemblealg,
    limits,
    trajectories_upper,
    trajectories_lower,
    maxiters_limits
)

```

`PIDESolution`オブジェクトを返します。

# 引数:

  * `maxiters`: トレーニングエポックの数。デフォルトは`300`
  * `trajectories`: トレーニングのためにシミュレーションされる軌跡の数。デフォルトは`100`

[SDEアルゴリズム](https://diffeq.sciml.ai/stable/solvers/sde_solve/)を使用するには、[`DeepBSDE`](@ref)を使用してください。
