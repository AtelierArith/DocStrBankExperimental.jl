```
HEOMsolve(M, ρ0, tlist; e_ops, solver, H_t, params, verbose, filename, inplace, SOLVEROptions...)
heomsolve(M, ρ0, tlist; e_ops, solver, H_t, params, verbose, filename, inplace, SOLVEROptions...)
```

補助密度演算子の時間発展を通常の常微分方程式に基づいて解きます。

# パラメータ

  * `M::AbstractHEOMLSMatrix` : HEOMモデルから与えられた行列
  * `ρ0::Union{QuantumObject,ADOs}` : システムの初期状態（密度行列）または初期補助密度演算子（`ADOs`）
  * `tlist::AbstractVector` : 解決プロセス中に解を保存する特定の時間点を示します。
  * `e_ops::Union{Nothing,AbstractVector}`: 期待値を計算するための演算子のリスト。
  * `solver::OrdinaryDiffEqAlgorithm` : パッケージ`DifferentialEquations.jl`のソルバー。デフォルトは`DP5()`。
  * `H_t::Union{Nothing,QuantumObjectEvolution}`: 時間依存のシステムハミルトニアンまたはリウビリアン。デフォルトは`nothing`。
  * `params`: ソルバーに渡すパラメータ。通常、この引数は`NamedTuple`またはパラメータの`AbstractVector`として表現されます。より高度な使用法では、任意のカスタム構造体を使用できます。
  * `verbose::Bool` : プロセス中に詳細な出力と進行状況バーを表示するかどうか。デフォルトは`true`。
  * `filename::String` : ファイル名が指定された場合、解決プロセス後に各時間点でのADOがJLD2ファイル "filename.jld2" に保存されます。
  * `inplace::Bool`: ODEProblemのインプレースバージョンを使用するかどうか。デフォルトは`true`。
  * `SOLVEROptions` : ソルバーのための追加オプション

# 注意事項

  * [`ADOs`](@ref)は、`kwargs`のキーワード引数`saveat`に依存して保存されます。
  * `e_ops`が指定されている場合、デフォルト値は`saveat=[tlist[end]]`（最終的な`ADOs`のみを保存）ですが、そうでない場合は`saveat=tlist`（`tlist`に対応する`ADOs`を保存）になります。`e_ops`と`saveat`を別々に指定することもできます。
  * `kwargs`のデフォルトの許容誤差は`reltol=1e-6`および`abstol=1e-8`として与えられます。
  * `solver`の詳細については、[`DifferentialEquations.jl` (ODE Solvers)](https://docs.sciml.ai/DiffEqDocs/stable/solvers/ode_solve/)を参照してください。
  * `SOLVEROptions`の詳細については、[`DifferentialEquations.jl` (Keyword Arguments)](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/)を参照してください。

# 戻り値

  * sol::TimeEvolutionHEOMSol : 階層的EOMの解。詳細は[`TimeEvolutionHEOMSol`](@ref)を参照してください。

!!! note
    `heomsolve`は`HEOMsolve`の同義語です。

