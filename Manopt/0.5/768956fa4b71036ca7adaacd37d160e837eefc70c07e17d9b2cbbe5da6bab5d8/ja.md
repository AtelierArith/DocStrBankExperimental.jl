```
ExactPenaltyMethodState{P,T} <: AbstractManoptSolverState
```

正確ペナルティ法を説明します。

# フィールド

  * `ϵ`: 精度許容誤差
  * `ϵ_min`: 精度許容誤差の下限
  * `p::P`: 現在の反復を格納する多様体 $\mathcal M$ 上の点
  * `ρ`: ペナルティパラメータ
  * `sub_problem::Union{AbstractManoptProblem, F}`: ソルバー用の問題または、割り当て可能またはインプレースの閉形式解関数を指定します。
  * `sub_state::Union{AbstractManoptProblem, F}`: 使用するサブソルバーを指定する状態。閉形式解の場合、関数のタイプを示します。
  * `stop::StoppingCriterion`: 停止基準が満たされていることを示すファンクタ
  * `u`: 制約違反のためのスムージングパラメータと閾値
  * `u_min`: 制約違反のためのスムージングパラメータと閾値の下限
  * `θ_ϵ`: 許容誤差パラメータのスケーリングファクター
  * `θ_ρ`: ペナルティパラメータのスケーリングファクター
  * `θ_u`: スムージングパラメータのスケーリングファクター

# コンストラクタ

```
ExactPenaltyMethodState(M::AbstractManifold, sub_problem, sub_state; kwargs...)
```

正確ペナルティ状態を構築します。

```
ExactPenaltyMethodState(M::AbstractManifold, sub_problem;
    evaluation=AllocatingEvaluation(), kwargs...
```

)

`sub_problem` が評価のタイプとして `evaluation` を持つ閉形式解である正確ペナルティ状態を構築します。

# キーワード引数

  * `ϵ=1e-3`
  * `ϵ_min=1e-6`
  * `ϵ_exponent=1 / 100`: スケーリングファクター $θ_ϵ$ のショートカット
  * `θ_ϵ=(ϵ_min / ϵ)^(ϵ_exponent)`
  * `u=1e-1`
  * `u_min=1e-6`
  * `u_exponent=1 / 100`: スケーリングファクター $θ_u$ のショートカット。
  * `θ_u=(u_min / u)^(u_exponent)`
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: 初期値を指定する多様体 $\mathcal M$ 上の点
  * `ρ=1.0`
  * `θ_ρ=0.3`
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(300)`[`|`](@ref StopWhenAny)`(`: 停止基準が満たされていることを示すファンクタ [`StopWhenSmallerOrEqual`](@ref)`(:ϵ, ϵ_min)`[`|`](@ref StopWhenAny)[`StopWhenChangeLess`](@ref)`(1e-10) )`

# 参照

[`exact_penalty_method`](@ref)
