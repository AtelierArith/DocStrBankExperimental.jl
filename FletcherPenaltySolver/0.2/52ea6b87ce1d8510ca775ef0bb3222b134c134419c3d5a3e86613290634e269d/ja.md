```
FPSSSolver(nlp::AbstractNLPModel [, x0 = nlp.meta.x0]; kwargs...)
FPSSSolver(stp::NLPStopping; kwargs...)
```

`fps_solve` 呼び出し中に使用されるすべての構造体を再編成する構造体です。`FPSSSolver` 構造体を返します。

# 引数

キーワード引数には以下が含まれる場合があります：

  * `stp::NLPStopping`: このアルゴリズムのワークフローのための `Stopping` 構造体；
  * `meta::AlgoData{T}`: [`AlgoData`](@ref) を参照；
  * `workspace`: ソルバー自体のために割り当てられたスペース；
  * `qdsolver`: 線形代数部分のためのソルバー構造体で、この部分のための割り当てを含みます。デフォルトは `LDLtSolver` ですが、代替として `IterativeSolver` があります；
  * `subproblem_solver::AbstractOptimizationSolver`: デフォルトは `subproblem_solver_correspondence[Symbol(meta.subproblem_solver)]`；
  * `sub_stats::GenericExecutionStats`: `subproblem_solver` の結果のための統計構造体；
  * `feasibility_solver`: デフォルトは `GNSolver`、[`GNSolver`](@ref) を参照；
  * `model::FletcherPenaltyNLP`: サブプロブレム；
  * `sub_stp::NLPStopping`: サブプロブレムのための `Stopping` 構造体。

注意：

  * `subproblem_solver` は `subproblem_solver_correspondence::Dict` からアクセス可能です。
  * `qdsolver` は辞書 `qdsolver_correspondence` からアクセス可能です。
