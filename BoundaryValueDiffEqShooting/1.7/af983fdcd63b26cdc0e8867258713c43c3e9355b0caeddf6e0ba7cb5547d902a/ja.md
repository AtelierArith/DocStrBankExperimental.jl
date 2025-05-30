```
Shooting(ode_alg; kwargs...)
Shooting(ode_alg, nlsolve; kwargs...)
Shooting(; ode_alg = nothing, nlsolve = nothing, jac_alg = nothing)
```

単一シューティング法は、BVPを初期値問題に還元し、IVPを解決します。

## 引数

  * `ode_alg`: IVPを解決するために使用するODEアルゴリズム。SciML `ODEProblem`インターフェースに準拠する任意のソルバーを使用できます！ （デフォルトは`nothing`で、`DifferentialEquations.jl`がロードされている場合はポリアルゴリズムを使用し、それ以外の場合はこれを指定する必要があります）
  * `nlsolve`: 内部非線形ソルバー。SciML `NonlinearProblem`インターフェースに準拠する任意のソルバーを使用できます。ソルバーの自動微分引数は無視され、カスタムヤコビアンアルゴリズムが使用されます。
  * `jac_alg`: 非線形ソルバーに使用されるヤコビアンアルゴリズム。これが設定されていない場合、`nlsolve.ad`が存在し、`nothing`でないかを確認します。存在する場合は、それを使用してヤコビアンを構築します。存在しない場合は、入力タイプと問題タイプに基づいて最適なアルゴリズムを使用しようとします。`BVPJacobianAlgorithm`が提供されている場合、`diffmode`のみが使用されます（可能であればデフォルトは`AutoForwardDiff`、そうでなければ`AutoFiniteDiff`）。
