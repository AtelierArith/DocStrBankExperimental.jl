```
MultipleShooting(; nshoots::Int, ode_alg = nothing, nlsolve = nothing,
    grid_coarsening = true, jac_alg = nothing)
MultipleShooting(nshoots::Int; kwargs...)
MultipleShooting(nshoots::Int, ode_alg; kwargs...)
MultipleShooting(nshoots::Int, ode_alg, nlsolve; kwargs...)
```

マルチプルシューティング法は、BVPを初期値問題に還元し、IVPを解決します。シングルシューティングよりもはるかに安定しています。

## 引数

  * `nshoots`: シューティングポイントの数。
  * `ode_alg`: IVPを解くために使用するODEアルゴリズム。SciML `ODEProblem`インターフェースに準拠する任意のソルバーを使用できます！ （デフォルトは`nothing`で、`DifferentialEquations.jl`がロードされている場合はポリアルゴリズムを使用し、それ以外の場合はこれを指定する必要があります）
  * `nlsolve`: 内部非線形ソルバー。SciML `NonlinearProblem`インターフェースに準拠する任意のソルバーを使用できます。
  * `jac_alg`: 非線形ソルバーに使用されるヤコビアンアルゴリズム。デフォルトは`BVPJacobianAlgorithm()`で、入力タイプと問題タイプに基づいて使用する最適なアルゴリズムを自動的に決定します。

      * `TwoPointBVProblem`の場合、`diffmode`のみが使用されます（可能であればデフォルトは`AutoSparse(AutoForwardDiff())`、それ以外の場合は`AutoSparse(AutoFiniteDiff())`）。
      * `BVProblem`の場合、`bc_diffmode`と`nonbc_diffmode`が使用されます。`nonbc_diffmode`については、可能であれば`AutoSparse(AutoForwardDiff())`、それ以外の場合は`AutoSparse(AutoFiniteDiff())`をデフォルトとします。`bc_diffmode`については、可能であれば`AutoForwardDiff`、それ以外の場合は`AutoFiniteDiff`をデフォルトとします。
  * `grid_coarsening`: 安定したIVP解を生成するためにマルチプルシューティンググリッドを粗くします。可能な選択肢：

      * `true`: グリッドサイズを半分にし、グリッドサイズが1に達するまで続けます。
      * `false`: グリッドを粗くしません。マルチプルシューティング問題を解決し、最終的にシングルシューティング問題を解決します。
      * `AbstractVector{<:Int}`または`Ntuple{N, <:Integer}`: 提供されたグリッド粗化を使用します。たとえば、`nshoots = 10`で`grid_coarsening = [5, 2]`の場合、グリッドは`[5, 2]`に粗くなります。グリッド粗化に`1`が含まれてはいけません。
      * `Function`: 現在のシューティングポイントの数を受け取り、次のシューティングポイントの数を返します。たとえば、`nshoots = 10`で`grid_coarsening = n -> n ÷ 2`の場合、グリッドは`[5, 2]`に粗くなります。

```
