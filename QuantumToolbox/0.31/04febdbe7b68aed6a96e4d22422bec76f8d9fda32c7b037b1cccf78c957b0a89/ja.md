```
smesolve(
    H::Union{AbstractQuantumObject{Operator},Tuple},
    ψ0::QuantumObject,
    tlist::AbstractVector,
    c_ops::Union{Nothing,AbstractVector,Tuple} = nothing,
    sc_ops::Union{Nothing,AbstractVector,Tuple,AbstractQuantumObject} = nothing;
    alg::Union{Nothing,StochasticDiffEqAlgorithm} = nothing,
    e_ops::Union{Nothing,AbstractVector,Tuple} = nothing,
    params = NullParameters(),
    rng::AbstractRNG = default_rng(),
    ntraj::Int = 500,
    ensemblealg::EnsembleAlgorithm = EnsembleThreads(),
    prob_func::Union{Function, Nothing} = nothing,
    output_func::Union{Tuple,Nothing} = nothing,
    progress_bar::Union{Val,Bool} = Val(true),
    store_measurement::Union{Val,Bool} = Val(false),
    kwargs...,
)
```

オープン量子システムの確率的マスター方程式の時間発展。これは次の確率微分方程式によって定義されます：

$$
d \rho (t) = -i [\hat{H}, \rho(t)] dt + \sum_i \mathcal{D}[\hat{C}_i] \rho(t) dt + \sum_n \mathcal{D}[\hat{S}_n] \rho(t) dt + \sum_n \mathcal{H}[\hat{S}_n] \rho(t) dW_n(t),
$$

ここで

$$
\mathcal{D}[\hat{O}] \rho = \hat{O} \rho \hat{O}^\dagger - \frac{1}{2} \{\hat{O}^\dagger \hat{O}, \rho\},
$$

はリンドブラッドスーパーオペレーターであり、

$$
\mathcal{H}[\hat{O}] \rho = \hat{O} \rho + \rho \hat{O}^\dagger - \mathrm{Tr}[\hat{O} \rho + \rho \hat{O}^\dagger] \rho,
$$

上記の $\hat{C}_i$ は純粋な消散に関連する崩壊オペレーターを表し、$\hat{S}_n$ は確率的共同オペレーターです。$dW_n(t)$ 項は $\hat{S}_n$ に関連する実ウィーナー増分です。詳細については [Wiseman2009Quantum](@cite) を参照してください。

# 引数

  * `H`: システムのハミルトニアン $\hat{H}$。これは [`QuantumObject`](@ref)、[`QuantumObjectEvolution`](@ref)、またはオペレーター-関数ペアの `Tuple` のいずれかです。
  * `ψ0`: システムの初期状態 $|\psi(0)\rangle$。これは [`Ket`](@ref)、[`Operator`](@ref) または [`OperatorKet`](@ref) のいずれかです。
  * `tlist`: システムの状態または期待値を保存する時間のリスト。
  * `c_ops`: 崩壊オペレーターのリスト $\{\hat{C}_i\}_i$。これは `Vector` または `Tuple` のいずれかです。
  * `sc_ops`: 確率的崩壊オペレーターのリスト $\{\hat{S}_n\}_n$。これは `Vector`、`Tuple` または [`AbstractQuantumObject`](@ref) のいずれかです。オペレーターが1つだけ提供される場合は、最後のケースを使用することをお勧めします。
  * `alg`: 確率微分方程式に使用するアルゴリズム。`sc_ops` が [`AbstractQuantumObject`](@ref) の場合はデフォルトで `SRIW1()`（対角ノイズ）、それ以外の場合は `SRA2()`（非対角ノイズ）です。
  * `e_ops`: 期待値を計算するためのオペレーターのリスト。これは `Vector` または `Tuple` のいずれかです。
  * `params`: ソルバーに渡すパラメータの `NullParameters`。
  * `rng`: 再現性のための乱数生成器。
  * `ntraj`: 使用する軌道の数。デフォルトは `500` です。
  * `ensemblealg`: 使用するアンサンブル法。デフォルトは `EnsembleThreads()` です。
  * `prob_func`: SDEProblem を生成するために使用する関数。
  * `output_func`: 単一の軌道の出力を生成するために使用する `Function`、（オプションの）`ProgressBar` オブジェクト、および（オプションの）`RemoteChannel` オブジェクトを含む `Tuple`。
  * `progress_bar`: 進捗バーを表示するかどうか。非 `Val` 型を使用すると型の不安定性が生じる可能性があります。
  * `store_measurement`: 測定期待値を保存するかどうか。デフォルトは `Val(false)` です。
  * `kwargs`: ODEProblem のキーワード引数。

# 注意事項

  * 状態は `kwargs` のキーワード引数 `saveat` に依存して保存されます。
  * `e_ops` が空の場合、デフォルト値は `saveat=tlist`（`tlist` に対応する状態を保存）であり、そうでない場合は `saveat=[tlist[end]]`（最終状態のみ保存）です。`e_ops` と `saveat` を別々に指定することもできます。
  * `kwargs` のデフォルトの許容誤差は `reltol=1e-2` および `abstol=1e-2` です。
  * `kwargs` に関する詳細については、[`DifferentialEquations.jl` (キーワード引数)](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/) を参照してください。

!!! tip "パフォーマンステップ"
    `sc_ops` に単一のオペレーターのみが含まれている場合、そのオペレーターのみを引数として渡すことをお勧めします。これにより、確率ノイズが対角になり、シミュレーションが速くなります。


# 戻り値

  * `sol::TimeEvolutionStochasticSol`: 時間発展の解。詳細は [`TimeEvolutionStochasticSol`](@ref) を参照してください。

```
