```julia
solve(
    prob::HighDimPDE.ParabolicPDEProblem,
    pdealg::HighDimPDE.NNStopping,
    sdealg;
    verbose,
    maxiters,
    trajectories,
    dt,
    ensemblealg,
    kwargs...
) -> NamedTuple{(:payoff, :stopping_time), <:Tuple{Any, Any}}

```

`payoff` と `stopping_time` を持つ NamedTuple を返します。

引数:

  * `sdealg`: [DifferentialEquations.jl](https://diffeq.sciml.ai/stable/solvers/sde_solve/) からの SDE ソルバー。提供されない場合、プレーンバニラの [DeepBSDE](https://arxiv.org/abs/1707.02568) メソッドが適用されます。提供される場合、PDE 問題に関連する SDE が、`sdealg` を使用して DifferentialEquations.jl のメソッドに依存して解かれます。[Ensemble solves](https://diffeq.sciml.ai/stable/features/ensemble/) を介して。利用可能な `sdealg` は [DifferentialEquations.jl doc](https://diffeq.sciml.ai/stable/solvers/sde_solve/) で確認してください。
  * `maxiters`: トレーニングエポックの数。デフォルトは `300`
  * `trajectories`: トレーニングのためにシミュレーションされる軌道の数。デフォルトは `100`
  * `solve` に渡される追加のキーワード引数は、SDE ソルバーにさらに渡されます。
