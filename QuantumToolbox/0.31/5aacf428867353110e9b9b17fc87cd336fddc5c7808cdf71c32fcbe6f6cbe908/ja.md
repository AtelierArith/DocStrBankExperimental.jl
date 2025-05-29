```
mcsolveProblem(
    H::Union{AbstractQuantumObject{Operator},Tuple},
    ψ0::QuantumObject{Ket},
    tlist::AbstractVector,
    c_ops::Union{Nothing,AbstractVector,Tuple} = nothing;
    e_ops::Union{Nothing,AbstractVector,Tuple} = nothing,
    params = NullParameters(),
    rng::AbstractRNG = default_rng(),
    jump_callback::TJC = ContinuousLindbladJumpCallback(),
    kwargs...,
)
```

オープン量子系のモンテカルロ波動関数の時間発展の単一軌道のODEProblemを生成します。

系のハミルトニアン $\hat{H}$ と崩壊（ジャンプ）演算子のリスト $\{\hat{C}_n\}_n$ が与えられたとき、状態 $|\psi(t)\rangle$ の時間発展はシュレディンガー方程式によって支配されます：

$$
\frac{\partial}{\partial t} |\psi(t)\rangle= -i \hat{H}_{\textrm{eff}} |\psi(t)\rangle
$$

非エルミートな効果的ハミルトニアンを用いて：

$$
\hat{H}_{\textrm{eff}} = \hat{H} - \frac{i}{2} \sum_n \hat{C}_n^\dagger \hat{C}_n.
$$

小さな時間 $\delta t$ における波動関数の一次の項に対して、$\hat{H}_{\textrm{eff}}$ の厳密に負の非エルミート部分は波動関数のノルムの減少を引き起こします。すなわち、

$$
\langle \psi(t+\delta t) | \psi(t+\delta t) \rangle = 1 - \delta p,
$$

ここで 

$$
\delta p = \delta t \sum_n \langle \psi(t) | \hat{C}_n^\dagger \hat{C}_n | \psi(t) \rangle
$$

は対応する量子ジャンプ確率です。

環境の測定が量子ジャンプを記録した場合、波動関数は測定に対応する崩壊演算子 $\hat{C}_n$ を用いて $|\psi(t)\rangle$ を射影することによって定義された状態にジャンプします。すなわち、

$$
| \psi(t+\delta t) \rangle = \frac{\hat{C}_n |\psi(t)\rangle}{ \sqrt{\langle \psi(t) | \hat{C}_n^\dagger \hat{C}_n | \psi(t) \rangle} }
$$

# 引数

  * `H`: 系のハミルトニアン $\hat{H}$。これは [`QuantumObject`](@ref)、[`QuantumObjectEvolution`](@ref)、または演算子-関数ペアの `Tuple` であることができます。
  * `ψ0`: 系の初期状態 $|\psi(0)\rangle$。
  * `tlist`: 状態または期待値を保存する時間のリスト。
  * `c_ops`: 崩壊演算子のリスト $\{\hat{C}_n\}_n$。これは `Vector` または `Tuple` であることができます。
  * `e_ops`: 期待値を計算するための演算子のリスト。これは `Vector` または `Tuple` であることができます。
  * `params`: ソルバーに渡すパラメータ。この引数は通常、パラメータの `NamedTuple` または `AbstractVector` として表現されます。より高度な使用法では、任意のカスタム構造体を使用できます。
  * `rng`: 再現性のための乱数生成器。
  * `jump_callback`: ジャンプコールバックのタイプ：離散または連続。デフォルトは `ContinuousLindbladJumpCallback()` で、より正確です。
  * `kwargs`: ODEProblem のキーワード引数。

# 注意事項

  * 状態は `kwargs` のキーワード引数 `saveat` に依存して保存されます。
  * `e_ops` が空の場合、デフォルト値は `saveat=tlist`（`tlist` に対応する状態を保存）ですが、そうでない場合は `saveat=[tlist[end]]`（最終状態のみ保存）になります。`e_ops` と `saveat` を別々に指定することもできます。
  * `kwargs` のデフォルトの許容誤差は `reltol=1e-6` と `abstol=1e-8` です。
  * `kwargs` に関する詳細については、[`DifferentialEquations.jl` (キーワード引数)](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/) を参照してください。

# 戻り値

  * `prob`: モンテカルロ波動関数の時間発展のための `ODEProblem` を含む [`TimeEvolutionProblem`](@ref)。
