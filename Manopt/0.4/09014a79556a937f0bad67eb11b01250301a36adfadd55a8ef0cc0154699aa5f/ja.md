```
AugmentedLagrangianMethodState{P,T} <: AbstractManoptSolverState
```

拡張ラグランジュ法を説明します。

# フィールド

パラメータを初期化時に省略できる場合、デフォルト値は括弧内に示されています。

  * `p`:                  マンフォールド上の点、開始点および現在の反復
  * `sub_problem`:        サブソルバーのための[`AbstractManoptProblem`](@ref)問題
  * `sub_state`:          サブソルバーのための[`AbstractManoptSolverState`](@ref)
  * `ϵ`:                  （`1e–3`）精度許容誤差
  * `ϵ_min`:              （`1e-6`）精度許容誤差の下限
  * `λ`:                  （`ones(n)`）等式制約に関するラグランジュ乗数
  * `λ_max`:              （`20.0`）等式制約に属するラグランジュ乗数の上限
  * `λ_min`:              （`- λ_max`）等式制約に属するラグランジュ乗数の下限
  * `μ`:                  （`ones(m)`）不等式制約に関するラグランジュ乗数
  * `μ_max`:              （`20.0`）不等式制約に属するラグランジュ乗数の上限
  * `ρ`:                  （`1.0`）ペナルティパラメータ
  * `τ`:                  （`0.8`）ペナルティパラメータの評価改善のための係数
  * `θ_ρ`:                （`0.3`）ペナルティパラメータのスケーリング係数
  * `θ_ϵ`:                （`(ϵ_min/ϵ)^(ϵ_exponent)`）精度許容誤差のスケーリング係数
  * `penalty`:            現在のペナルティ項の評価、初期値は`Inf`。
  * `stop`: （（[`StopAfterIteration`](@ref)`(300) | （[`StopWhenSmallerOrEqual`](@ref)`(ϵ, ϵ_min) &`[`StopWhenChangeLess`](@ref)`(1e-10))））[`StoppingCriterion`](@ref)から継承されたファンクタで、停止するタイミングを示します。

# コンストラクタ

```
AugmentedLagrangianMethodState(M::AbstractManifold, co::ConstrainedManifoldObjective, p; kwargs...)
```

前述のフィールドとデフォルトを持つ拡張ラグランジュ法のオプションを構築します。ここで、マンフォールド`M`と[`ConstrainedManifoldObjective`](@ref) `co`は、マンフォールドまたは目的特有のデフォルトに役立ちます。

# 参照

[`augmented_Lagrangian_method`](@ref)
