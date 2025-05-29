```
ODESolver(solver, kwargs..)
```

ODEソルバーオプション（`solver`、`tolerances`など）は、`PEtabODEProblem`内のODEモデルを解くために使用されます。

[OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl)および[Sundials.jl](https://github.com/SciML/Sundials.jl)のいずれかの`solver`がサポートされています。`PEtabODEProblem`を作成する際に`ODESolver`が提供されていない場合に使用されるソルバーの推奨事項やデフォルトオプションについては、ドキュメントを参照してください。

利用可能なオプションやソルバーに関する詳細情報は、[DifferentialEquations.jl](https://docs.sciml.ai/DiffEqDocs/stable/solvers/ode_solve/)のドキュメントにも記載されています。

# キーワード引数

  * `abstol=1e-8`: ODEモデルを解く際の絶対許容誤差。正確な勾配を得るためには、1e-6を超えて増加させることは推奨されません。
  * `reltol=1e-8`: ODEモデルを解く際の相対許容誤差。正確な勾配を得るためには、1e-6を超えて増加させることは推奨されません。
  * `dtmin=nothing`: ODEモデルを解く際の最小許容ステップサイズ。
  * `maxiters=10000`: ODEモデルを解く際の最大反復回数。デフォルト値を超えて増加させると、パラメータ推定にかなりの時間がかかる可能性があります。
  * `verbose::Bool=true`: ソルバーが早期に終了した場合に警告を表示するかどうか。`true`は、最適でない`solver`の選択を検出するために推奨されます。
  * `adj_solver=solver`: 隣接ODEを解く際に使用するソルバー。`PEtabODEProblem`を作成する際に`gradient_method=:Adjoint`の場合にのみ適用されます。デフォルトは`solver`です。
  * `abstol_adj=abstol`: 隣接ODEモデルを解く際の絶対許容誤差。`PEtabODEProblem`を作成する際に`gradient_method=:Adjoint`の場合にのみ適用されます。デフォルトは`abstol`です。
  * `reltol_adj=abstol`: 隣接ODEモデルを解く際の相対許容誤差。`PEtabODEProblem`を作成する際に`gradient_method=:Adjoint`の場合にのみ適用されます。デフォルトは`reltol`です。
