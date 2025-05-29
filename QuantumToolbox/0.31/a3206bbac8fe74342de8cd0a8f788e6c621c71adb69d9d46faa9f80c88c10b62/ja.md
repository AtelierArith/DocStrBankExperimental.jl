```
mcsolve(
    H::Union{AbstractQuantumObject{Operator},Tuple},
    ψ0::QuantumObject{Ket},
    tlist::AbstractVector,
    c_ops::Union{Nothing,AbstractVector,Tuple} = nothing;
    alg::OrdinaryDiffEqAlgorithm = Tsit5(),
    e_ops::Union{Nothing,AbstractVector,Tuple} = nothing,
    params = NullParameters(),
    rng::AbstractRNG = default_rng(),
    ntraj::Int = 500,
    ensemblealg::EnsembleAlgorithm = EnsembleThreads(),
    jump_callback::TJC = ContinuousLindbladJumpCallback(),
    progress_bar::Union{Val,Bool} = Val(true),
    prob_func::Union{Function, Nothing} = nothing,
    output_func::Union{Tuple,Nothing} = nothing,
    normalize_states::Union{Val,Bool} = Val(true),
    kwargs...,
)

オープン量子系の時間発展を量子軌道を用いて行います。

系のハミルトニアン $\hat{H}$ と崩壊（ジャンプ）演算子のリスト $\{\hat{C}_n\}_n$ が与えられたとき、状態 $|\psi(t)\rangle$ の発展はシュレディンガー方程式によって支配されます：

```

math \frac{\partial}{\partial t} |\psi(t)\rangle= -i \hat{H}_{\textrm{eff}} |\psi(t)\rangle

```

非エルミートな有効ハミルトニアンを用いて：

```

math \hat{H}*{\textrm{eff}} = \hat{H} - \frac{i}{2} \sum*n \hat{C}*n^\dagger \hat{C}*n.

```

小さな時間 $\delta t$ における波動関数の一次の項に対して、$\hat{H}_{\textrm{eff}}$ の厳密に負の非エルミート部分は波動関数のノルムの減少を引き起こします。すなわち、

```

math \langle \psi(t+\delta t) | \psi(t+\delta t) \rangle = 1 - \delta p,

```

ここで 

```

math \delta p = \delta t \sum*n \langle \psi(t) | \hat{C}*n^\dagger \hat{C}_n | \psi(t) \rangle

```

は対応する量子ジャンプ確率です。

環境の測定が量子ジャンプを記録した場合、波動関数は測定に対応する崩壊演算子 $\hat{C}_n$ を用いて $|\psi(t)\rangle$ を射影することによって定義された状態にジャンプします。すなわち、

```

math | \psi(t+\delta t) \rangle = \frac{\hat{C}*n |\psi(t)\rangle}{ \sqrt{\langle \psi(t) | \hat{C}*n^\dagger \hat{C}_n | \psi(t) \rangle} }

```

# 引数

  * `H`: 系のハミルトニアン $\hat{H}$。これは [`QuantumObject`](@ref)、[`QuantumObjectEvolution`](@ref)、または演算子-関数ペアの `Tuple` であることができます。
  * `ψ0`: 系の初期状態 $|\psi(0)\rangle$。
  * `tlist`: 状態または期待値を保存する時間のリスト。
  * `c_ops`: 崩壊演算子のリスト $\{\hat{C}_n\}_n$。これは `Vector` または `Tuple` であることができます。
  * `alg`: ODEソルバーに使用するアルゴリズム。デフォルトは `Tsit5()`。
  * `e_ops`: 期待値を計算するための演算子のリスト。これは `Vector` または `Tuple` であることができます。
  * `params`: ソルバーに渡すパラメータ。この引数は通常、パラメータの `NamedTuple` または `AbstractVector` として表現されます。より高度な使用法では、任意のカスタム構造体を使用できます。
  * `rng`: 再現性のための乱数生成器。
  * `ntraj`: 使用する軌道の数。
  * `ensemblealg`: 使用するアンサンブルアルゴリズム。デフォルトは `EnsembleThreads()`。
  * `jump_callback`: ジャンプコールバックのタイプ：離散または連続。デフォルトは `ContinuousLindbladJumpCallback()` で、より正確です。
  * `progress_bar`: 進捗バーを表示するかどうか。非 `Val` 型を使用すると型の不安定性が生じる可能性があります。
  * `prob_func`: ODEProblemを生成するために使用する関数。
  * `output_func`: 単一の軌道の出力を生成するために使用する `Function`、（オプションの）`ProgressBar` オブジェクト、および（オプションの）`RemoteChannel` オブジェクトを含む `Tuple`。
  * `normalize_states`: 状態を正規化するかどうか。デフォルトは `Val(true)`。
  * `kwargs`: ODEProblemのキーワード引数。

# 注意事項

  * `ensemblealg` は `EnsembleThreads()`、`EnsembleSerial()`、`EnsembleDistributed()` のいずれかであることができます。
  * 状態は `kwargs` のキーワード引数 `saveat` に依存して保存されます。
  * `e_ops` が空の場合、デフォルト値は `saveat=tlist`（`tlist` に対応する状態を保存）ですが、そうでない場合は `saveat=[tlist[end]]`（最終状態のみを保存）になります。`e_ops` と `saveat` を別々に指定することもできます。
  * `kwargs` のデフォルトの許容誤差は `reltol=1e-6` および `abstol=1e-8` として与えられます。
  * `alg` に関する詳細については、[`DifferentialEquations.jl` (ODE Solvers)](https://docs.sciml.ai/DiffEqDocs/stable/solvers/ode_solve/) を参照してください。
  * `kwargs` に関する詳細については、[`DifferentialEquations.jl` (Keyword Arguments)](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/) を参照してください。

# 戻り値

  * `sol::TimeEvolutionMCSol`: 時間発展の解。詳細は [`TimeEvolutionMCSol`](@ref) を参照してください。
```
