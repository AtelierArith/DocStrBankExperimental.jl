```julia
solve(
    prob::HighDimPDE.ParabolicPDEProblem,
    pdealg::HighDimPDE.DeepBSDE,
    sdealg;
    verbose,
    maxiters,
    trajectories,
    dt,
    pabstol,
    save_everystep,
    limits,
    ensemblealg,
    trajectories_upper,
    trajectories_lower,
    maxiters_limits,
    kwargs...
) -> Any

```

`PIDESolution`オブジェクトを返します。

# 引数

  * `sdealg`: [DifferentialEquations.jl](https://diffeq.sciml.ai/stable/solvers/sde_solve/)からのSDEソルバー。提供されない場合、プレーンバニラの[DeepBSDE](https://arxiv.org/abs/1707.02568)メソッドが適用されます。提供された場合、PDE問題に関連するSDEが、`sdealg`を使用してDifferentialEquations.jlのメソッドに依存して解決されます。[Ensemble solves](https://diffeq.sciml.ai/stable/features/ensemble/)を介して。利用可能な`sdealg`については、[DifferentialEquations.jlのドキュメント](https://diffeq.sciml.ai/stable/solvers/sde_solve/)を確認してください。
  * `limits`: `true`の場合、[Deep Primal-Dual algorithm for BSDEs](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3071506)に基づいて上限と下限が計算されます。
  * `maxiters`: トレーニングエポックの数。デフォルトは`300`
  * `trajectories`: トレーニングのためにシミュレーションされる軌跡の数。デフォルトは`100`
  * `solve`に渡される追加のキーワード引数は、SDEソルバーにさらに渡されます。
