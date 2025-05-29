```
ssesolveProblem(
    H::Union{AbstractQuantumObject{Operator},Tuple},
    ψ0::QuantumObject{Ket},
    tlist::AbstractVector,
    sc_ops::Union{Nothing,AbstractVector,Tuple,AbstractQuantumObject} = nothing;
    e_ops::Union{Nothing,AbstractVector,Tuple} = nothing,
    params = NullParameters(),
    rng::AbstractRNG = default_rng(),
    progress_bar::Union{Val,Bool} = Val(true),
    store_measurement::Union{Val, Bool} = Val(false),
    kwargs...,
)
```

量子系の確率的シュレーディンガー時間発展のためのSDEProblemを生成します。これは以下の確率微分方程式によって定義されます：

$$
d|\psi(t)\rangle = -i \hat{K} |\psi(t)\rangle dt + \sum_n \hat{M}_n |\psi(t)\rangle dW_n(t)
$$

ここで 

$$
\hat{K} = \hat{H} + i \sum_n \left(\frac{e_n}{2} \hat{S}_n - \frac{1}{2} \hat{S}_n^\dagger \hat{S}_n - \frac{e_n^2}{8}\right),
$$

$$
\hat{M}_n = \hat{S}_n - \frac{e_n}{2},
$$

および

$$
e_n = \langle \hat{S}_n + \hat{S}_n^\dagger \rangle.
$$

上記の$\hat{S}_n$は確率的崩壊演算子であり、$dW_n(t)$は$\hat{S}_n$に関連する実ウィーナー増分です。詳細については[Wiseman2009Quantum](@cite)を参照してください。

# 引数

  * `H`: 系のハミルトニアン$\hat{H}$。これは[`QuantumObject`](@ref)、[`QuantumObjectEvolution`](@ref)、または演算子-関数ペアの`Tuple`のいずれかです。
  * `ψ0`: 系の初期状態$|\psi(0)\rangle$。
  * `tlist`: 状態または期待値を保存する時間のリスト。
  * `sc_ops`: 確率的崩壊演算子のリスト$\{\hat{S}_n\}_n$。これは`Vector`、`Tuple`、または[`AbstractQuantumObject`](@ref)のいずれかです。演算子が1つだけ提供される場合は、最後のケースを使用することをお勧めします。
  * `e_ops`: 期待値を計算するための演算子のリスト。これは`Vector`または`Tuple`のいずれかです。
  * `params`: ソルバーに渡すパラメータの`NullParameters`。
  * `rng`: 再現性のための乱数生成器。
  * `progress_bar`: 進捗バーを表示するかどうか。非`Val`型を使用すると型の不安定性が生じる可能性があります。
  * `store_measurement`: 測定結果を保存するかどうか。デフォルトは`Val(false)`です。
  * `kwargs`: ODEProblemのためのキーワード引数。

# 注意事項

  * 状態は`kwargs`のキーワード引数`saveat`に依存して保存されます。
  * `e_ops`が空の場合、デフォルト値は`saveat=tlist`（`tlist`に対応する状態を保存）ですが、そうでない場合は`saveat=[tlist[end]]`（最終状態のみ保存）になります。`e_ops`と`saveat`を別々に指定することもできます。
  * `kwargs`のデフォルトの許容誤差は`reltol=1e-2`および`abstol=1e-2`です。
  * `kwargs`の詳細については、[`DifferentialEquations.jl` (キーワード引数)](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/)を参照してください。

!!! tip "パフォーマンステップ"
    `sc_ops`に単一の演算子のみが含まれている場合、その演算子のみを引数として渡すことをお勧めします。これにより、確率的ノイズが対角化され、シミュレーションが速くなります。


# 戻り値

  * `prob`: 系の確率的シュレーディンガー時間発展のための`SDEProblem`。
