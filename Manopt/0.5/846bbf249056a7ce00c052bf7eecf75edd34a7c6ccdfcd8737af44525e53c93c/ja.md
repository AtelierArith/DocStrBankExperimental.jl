```
AugmentedLagrangianMethodState{P,T} <: AbstractManoptSolverState
```

拡張ラグランジュ法を説明します。

# フィールド

パラメータを初期化時に省略できる場合、デフォルト値は括弧内に示されます。

  * `ϵ`:     精度の許容範囲
  * `ϵ_min`: 精度の許容範囲の下限
  * `λ`:     等式制約に関するラグランジュ乗数
  * `λ_max`: 等式制約に属するラグランジュ乗数の上限
  * `λ_min`: 等式制約に属するラグランジュ乗数の下限
  * `p::P`: マニフォールド $\mathcal M$ 上の点で、現在の反復を格納します
  * `penalty`: 現在のペナルティ項の評価、初期値は `Inf`。
  * `μ`:     不等式制約に関するラグランジュ乗数
  * `μ_max`: 不等式制約に属するラグランジュ乗数の上限
  * `ρ`:     ペナルティパラメータ
  * `sub_problem::Union{AbstractManoptProblem, F}`: ソルバー用の問題または閉形式の解関数を指定します。割り当て可能またはインプレースであることができます。
  * `sub_state::Union{AbstractManoptProblem, F}`: 使用するサブソルバーを指定する状態。閉形式の解の場合、関数の型を示します。
  * `τ`:     ペナルティパラメータの評価改善のための係数
  * `θ_ρ`:   ペナルティパラメータのスケーリング係数
  * `θ_ϵ`:   精度の許容範囲のスケーリング係数
  * `stop::StoppingCriterion`: 停止基準が満たされていることを示すファンクタ

# コンストラクタ

```
AugmentedLagrangianMethodState(M::AbstractManifold, co::ConstrainedManifoldObjective,
    sub_problem, sub_state; kwargs...
)
```

拡張ラグランジュ法のオプションを構築します。ここで、マニフォールド `M` と [`ConstrainedManifoldObjective`](@ref) `co` は、マニフォールドまたは目的特有のデフォルトに使用されます。

```
AugmentedLagrangianMethodState(M::AbstractManifold, co::ConstrainedManifoldObjective,
    sub_problem; evaluation=AllocatingEvaluation(), kwargs...
)
```

拡張ラグランジュ法のオプションを構築します。ここで、マニフォールド `M` と [`ConstrainedManifoldObjective`](@ref) `co` は、マニフォールドまたは目的特有のデフォルトに使用され、`sub_problem` は `evaluation` を評価の型とする閉形式の解です。

## キーワード引数

次のキーワード引数が利用可能で、対応するフィールドを初期化します。

  * `ϵ=1e–3`
  * `ϵ_min=1e-6`
  * `λ=ones(n)`: `n` は [`ConstrainedManifoldObjective`](@ref) `co` における等式制約の数です。
  * `λ_max=20.0`
  * `λ_min=- λ_max`
  * `μ=ones(m)`: `m` は [`ConstrainedManifoldObjective`](@ref) `co` における不等式制約の数です。
  * `μ_max=20.0`
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: 初期値を指定するためのマニフォールド $\mathcal M$ 上の点
  * `ρ=1.0`
  * `τ=0.8`
  * `θ_ρ=0.3`
  * `θ_ϵ=(ϵ_min/ϵ)^(ϵ_exponent)`
  * stopping*criterion=[`StopAfterIteration`](@ref)`(300)`[`|`](@ref StopWhenAny)([`StopWhenSmallerOrEqual`](@ref)`(:ϵ, ϵ*min)`[` & `](@ref StopWhenAll)[`StopWhenChangeLess`](@ref)`(1e-10) )`[` | `](@ref StopWhenAny)[`StopWhenChangeLess`](@ref)`.

# 参照

[`augmented_Lagrangian_method`](@ref)
