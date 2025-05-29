```
smesolveProblem(
    H::Union{AbstractQuantumObject{Operator},Tuple},
    ψ0::QuantumObject,
    tlist::AbstractVector,
    c_ops::Union{Nothing,AbstractVector,Tuple} = nothing,
    sc_ops::Union{Nothing,AbstractVector,Tuple,AbstractQuantumObject} = nothing;
    e_ops::Union{Nothing,AbstractVector,Tuple} = nothing,
    params = NullParameters(),
    rng::AbstractRNG = default_rng(),
    progress_bar::Union{Val,Bool} = Val(true),
    store_measurement::Union{Val, Bool} = Val(false),
    kwargs...,
)

確率的マスター方程式の時間発展のためのSDEProblemを生成します。これは以下の確率微分方程式によって定義されます：

```

math d \rho (t) = -i [\hat{H}, \rho(t)] dt + \sum*i \mathcal{D}[\hat{C}*i] \rho(t) dt + \sum*n \mathcal{D}[\hat{S}*n] \rho(t) dt + \sum*n \mathcal{H}[\hat{S}*n] \rho(t) dW_n(t),

```

ここで

```

math \mathcal{D}[\hat{O}] \rho = \hat{O} \rho \hat{O}^\dagger - \frac{1}{2} {\hat{O}^\dagger \hat{O}, \rho},

```

はリンドブラッドスーパーオペレーターであり、

```

math \mathcal{H}[\hat{O}] \rho = \hat{O} \rho + \rho \hat{O}^\dagger - \mathrm{Tr}[\hat{O} \rho + \rho \hat{O}^\dagger] \rho,

```

上記の$\hat{C}_i$は純粋な消散に関連する崩壊オペレーターを表し、$\hat{S}_n$は確率的崩壊オペレーターです。$dW_n(t)$項は$\hat{S}_n$に関連する実ウィーナー増分です。詳細については[Wiseman2009Quantum](@cite)を参照してください。

# 引数

  * `H`: システムのハミルトニアン$\hat{H}$。これは[`QuantumObject`](@ref)、[`QuantumObjectEvolution`](@ref)、またはオペレーター-関数ペアの`Tuple`のいずれかです。
  * `ψ0`: システムの初期状態$|\psi(0)\rangle$。これは[`Ket`](@ref)、[`Operator`](@ref)または[`OperatorKet`](@ref)のいずれかです。
  * `tlist`: システムの状態または期待値を保存する時間のリスト。
  * `c_ops`: 崩壊オペレーターのリスト$\{\hat{C}_i\}_i$。これは`Vector`または`Tuple`のいずれかです。
  * `sc_ops`: 確率的崩壊オペレーターのリスト$\{\hat{S}_n\}_n$。これは`Vector`、`Tuple`または[`AbstractQuantumObject`](@ref)のいずれかです。オペレーターが1つだけ提供される場合は、最後のケースを使用することをお勧めします。
  * `e_ops`: 期待値を計算するためのオペレーターのリスト。これは`Vector`または`Tuple`のいずれかです。
  * `params`: ソルバーに渡すパラメータの`NullParameters`。
  * `rng`: 再現性のための乱数生成器。
  * `progress_bar`: 進捗バーを表示するかどうか。非`Val`型を使用すると型の不安定性が生じる可能性があります。
  * `store_measurement`: 測定期待値を保存するかどうか。デフォルトは`Val(false)`です。
  * `kwargs`: ODEProblemのためのキーワード引数。

# 注意事項

  * 状態は`kwargs`のキーワード引数`saveat`に依存して保存されます。
  * `e_ops`が空の場合、デフォルト値は`saveat=tlist`（`tlist`に対応する状態を保存）であり、そうでない場合は`saveat=[tlist[end]]`（最終状態のみを保存）です。`e_ops`と`saveat`を別々に指定することもできます。
  * `kwargs`のデフォルトの許容誤差は`reltol=1e-2`および`abstol=1e-2`として与えられます。
  * `kwargs`の詳細については、[`DifferentialEquations.jl` (キーワード引数)](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/)を参照してください。

!!! tip "パフォーマンステップ"
    `sc_ops`が単一のオペレーターのみを含む場合、そのオペレーターのみを引数として渡すことをお勧めします。これにより、確率的ノイズが対角化され、シミュレーションが速くなります。

# 戻り値

  * `prob`: 確率的マスター方程式の時間発展のための`SDEProblem`を含む[`TimeEvolutionProblem`](@ref)。
```
