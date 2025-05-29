```
ExactPenaltyMethodState{P,T} <: AbstractManoptSolverState
```

正確ペナルティ法を説明します。

# フィールド

初期化時にパラメータを省略できる場合、デフォルト値は括弧内に示されます。

  * `p`:                   マニフォールド上のセットポイント（開始点）
  * `sub_problem`:         サブソルバーのための[`AbstractManoptProblem`](@ref)問題
  * `sub_state`:           サブソルバーのための[`AbstractManoptSolverState`](@ref)
  * `ϵ`:                   （`1e–3`）精度許容値
  * `ϵ_min`:               （`1e-6`）精度許容値の下限
  * `u`:                   （`1e–1`）スムージングパラメータおよび制約違反の閾値
  * `u_min`:               （`1e-6`）スムージングパラメータおよび制約違反の閾値の下限
  * `ρ`:                   （`1.0`）ペナルティパラメータ
  * `θ_ρ`:                 （`0.3`）ペナルティパラメータのスケーリングファクター
  * `stopping_criterion`:  ([`StopAfterIteration`](@ref)`(300) | (`[`StopWhenSmallerOrEqual`](@ref)`(ϵ, ϵ_min) &`[`StopWhenChangeLess`](@ref)`(min_stepsize))`) 停止条件を示す[`StoppingCriterion`](@ref)から継承されたファンクタ。

# コンストラクタ

```
ExactPenaltyMethodState(M::AbstractManifold, p, sub_problem, sub_state; kwargs...)
```

提供されたデフォルトを使用して、残りの前述のフィールドをキーワードとして持つ正確なペナルティオプションを構築します。

# 参照

[`exact_penalty_method`](@ref)
