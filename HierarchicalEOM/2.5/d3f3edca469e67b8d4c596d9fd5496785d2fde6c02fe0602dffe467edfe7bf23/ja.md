```
steadystate(M::AbstractHEOMLSMatrix, ρ0, tspan; solver, verbose, SOLVEROptions...)
```

時間発展に基づいて補助密度演算子の定常状態を解きます（`OrdinaryDiffEq.jl`）、初期状態は密度行列の型で与えられます（`ρ0`）。

# パラメータ

  * `M::AbstractHEOMLSMatrix` : HEOMモデルから与えられる行列で、パリティは`EVEN`である必要があります。
  * `ρ0::Union{QuantumObject,ADOs}` : システムの初期状態（密度行列）または初期補助密度演算子（`ADOs`）
  * `tspan::Number` : 定常状態を見つけるための時間制限。デフォルトは`Inf`
  * `solver::OrdinaryDiffEqAlgorithm` : パッケージ`DifferentialEquations.jl`のODEソルバー。デフォルトは`DP5()`。
  * `verbose::Bool` : プロセス中に詳細な出力と進行状況バーを表示するかどうか。デフォルトは`true`。
  * `SOLVEROptions` : ソルバーのための追加オプション

# 注意事項

  * `solver`に関する詳細については、[`DifferentialEquations.jl` (ODE Solvers)](https://docs.sciml.ai/DiffEqDocs/stable/solvers/ode_solve/)を参照してください。
  * `SOLVEROptions`に関する詳細については、[`DifferentialEquations.jl` (Keyword Arguments)](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/)を参照してください。

# 戻り値

  * `::ADOs` : 補助密度演算子の定常状態。

```
