```julia
solve(
    prob::HighDimPDE.ParabolicPDEProblem,
    pdealg::HighDimPDE.NNParamKolmogorov;
    ...
)
solve(
    prob::HighDimPDE.ParabolicPDEProblem,
    pdealg::HighDimPDE.NNParamKolmogorov,
    sdealg;
    ensemblealg,
    abstol,
    verbose,
    maxiters,
    trajectories,
    save_everystep,
    use_gpu,
    dps,
    dt,
    dx,
    kwargs...
)

```

`PIDESolution`オブジェクトを返します。

# 引数

  * `sdealg`: [DifferentialEquations.jl](https://diffeq.sciml.ai/stable/solvers/sde_solve/)からのSDEソルバー。提供されない場合、プレーンバニラの[DeepBSDE](https://arxiv.org/abs/1707.02568)メソッドが適用されます。提供される場合、PDE問題に関連するSDEが、`sdealg`を使用してDifferentialEquations.jlのメソッドに依存して解決されます。[Ensemble solves](https://diffeq.sciml.ai/stable/features/ensemble/)を介して。利用可能な`sdealg`は、[DifferentialEquations.jlのドキュメント](https://diffeq.sciml.ai/stable/solvers/sde_solve/)で確認してください。
  * `maxiters`: トレーニングエポックの数。デフォルトは`300`
  * `trajectories`: トレーニングのためにシミュレートされる軌道の数。デフォルトは`100`
  * `dps::NamedTuple`: パラメータの範囲のサンプリング間隔。キーは`:p_sigma`、`p*mu`および`p*phi`を持つ必要があります。
  * `solve`に渡される追加のキーワード引数は、SDEソルバーにさらに渡されます。
