```
sesolve(
    H::Union{AbstractQuantumObject{Operator},Tuple},
    ψ0::QuantumObject{Ket},
    tlist::AbstractVector;
    alg::OrdinaryDiffEqAlgorithm = Tsit5(),
    e_ops::Union{Nothing,AbstractVector,Tuple} = nothing,
    params = NullParameters(),
    progress_bar::Union{Val,Bool} = Val(true),
    inplace::Union{Val,Bool} = Val(true),
    kwargs...,
)

閉じた量子系の時間発展をシュレーディンガー方程式を用いて行います：

```

math \frac{\partial}{\partial t} |\psi(t)\rangle = -i \hat{H} |\psi(t)\rangle

```

# 引数

  * `H`: 系のハミルトニアン $\hat{H}$。これは [`QuantumObject`](@ref)、[`QuantumObjectEvolution`](@ref)、または演算子-関数ペアの `Tuple` のいずれかです。
  * `ψ0`: 系の初期状態 $|\psi(0)\rangle$。
  * `tlist`: 状態または期待値を保存する時間のリスト。
  * `alg`: ODEソルバーのアルゴリズム。デフォルトは `Tsit5()` です。
  * `e_ops`: 期待値を計算するための演算子のリスト。これは `Vector` または `Tuple` のいずれかです。
  * `params`: ソルバーに渡すパラメータ。通常、この引数はパラメータの `NamedTuple` または `AbstractVector` として表現されます。より高度な使用法では、任意のカスタム構造体を使用できます。
  * `progress_bar`: プログレスバーを表示するかどうか。非 `Val` 型を使用すると型の不安定性が生じる可能性があります。
  * `inplace`: ODEProblemのインプレースバージョンを使用するかどうか。デフォルトは `Val(true)` です。パフォーマンス向上のために `Val(true)` を使用することが推奨されますが、例えば [Zygote.jl](https://github.com/FluxML/Zygote.jl) を使用して自動微分を行う場合など、`Val(false)` を使用する必要があることもあります。
  * `kwargs`: ODEProblemのキーワード引数。

# 注意事項

  * 状態は `kwargs` のキーワード引数 `saveat` に依存して保存されます。
  * `e_ops` が空の場合、デフォルト値は `saveat=tlist`（`tlist` に対応する状態を保存）ですが、そうでない場合は `saveat=[tlist[end]]`（最終状態のみ保存）になります。`e_ops` と `saveat` を別々に指定することもできます。
  * `kwargs` のデフォルトの許容誤差は `reltol=1e-6` と `abstol=1e-8` です。
  * `alg` についての詳細は [`DifferentialEquations.jl` (ODE Solvers)](https://docs.sciml.ai/DiffEqDocs/stable/solvers/ode_solve/) を参照してください。
  * `kwargs` についての詳細は [`DifferentialEquations.jl` (Keyword Arguments)](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/) を参照してください。

# 戻り値

  * `sol::TimeEvolutionSol`: 時間発展の解。詳細は [`TimeEvolutionSol`](@ref) を参照してください。
```
