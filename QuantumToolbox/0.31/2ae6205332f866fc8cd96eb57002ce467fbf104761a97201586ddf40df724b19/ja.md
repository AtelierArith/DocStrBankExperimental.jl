```
sesolveProblem(
    H::Union{AbstractQuantumObject{Operator},Tuple},
    ψ0::QuantumObject{Ket},
    tlist::AbstractVector;
    e_ops::Union{Nothing,AbstractVector,Tuple} = nothing,
    params = NullParameters(),
    progress_bar::Union{Val,Bool} = Val(true),
    inplace::Union{Val,Bool} = Val(true),
    kwargs...,
)
```

量子系のシュレーディンガー時間発展のためのODEProblemを生成します：

$$
\frac{\partial}{\partial t} |\psi(t)\rangle = -i \hat{H} |\psi(t)\rangle
$$

# 引数

  * `H`: 系のハミルトニアン $\hat{H}$。これは、[`QuantumObject`](@ref)、[`QuantumObjectEvolution`](@ref)、または演算子-関数ペアの`Tuple`のいずれかです。
  * `ψ0`: 系の初期状態 $|\psi(0)\rangle$。
  * `tlist`: 状態または期待値を保存する時間のリスト。
  * `e_ops`: 期待値を計算するための演算子のリスト。これは、`Vector`または`Tuple`のいずれかです。
  * `params`: ソルバーに渡すパラメータ。この引数は通常、パラメータの`NamedTuple`または`AbstractVector`として表現されます。より高度な使用法では、任意のカスタム構造体を使用できます。
  * `progress_bar`: 進捗バーを表示するかどうか。非`Val`型を使用すると型の不安定性が生じる可能性があります。
  * `inplace`: ODEProblemのインプレースバージョンを使用するかどうか。デフォルトは`Val(true)`です。パフォーマンス向上のために`Val(true)`を使用することが推奨されますが、例えば[Zygote.jl](https://github.com/FluxML/Zygote.jl)を使用して自動微分を行う場合など、`Val(false)`を使用する必要があることもあります。
  * `kwargs`: ODEProblemのキーワード引数。

# 注意事項

  * 状態は、`kwargs`のキーワード引数`saveat`に依存して保存されます。
  * `e_ops`が空の場合、デフォルト値は`saveat=tlist`（`tlist`に対応する状態を保存）ですが、そうでない場合は`saveat=[tlist[end]]`（最終状態のみを保存）になります。`e_ops`と`saveat`を別々に指定することもできます。
  * `kwargs`のデフォルトの許容誤差は`reltol=1e-6`および`abstol=1e-8`として設定されています。
  * `kwargs`の詳細については、[`DifferentialEquations.jl` (キーワード引数)](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/)を参照してください。

# 戻り値

  * `prob`: 系のシュレーディンガー時間発展のための`ODEProblem`を含む[`TimeEvolutionProblem`](@ref)。
