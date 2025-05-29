```
QuasiNewtonState <: AbstractManoptSolverState
```

The [`AbstractManoptSolverState`](@ref) は任意の準ニュートンベースのメソッドを表し、すべての必要なフィールドを格納します。

# フィールド

  * `direction_update`:              [`AbstractQuasiNewtonDirectionUpdate`](@ref) ルール。
  * `η`:                             現在の更新方向
  * `nondescent_direction_behavior`: 降下方向でない方向を処理する方法を指定する `Symbol`。
  * `nondescent_direction_value`:    降下方向をチェックする際の最後の内積からの値
  * `p::P`: マニフォールド $\mathcal M$ 上の点で、現在の反復を格納
  * `p_old`:                         最後の反復
  * `preconditioner`                 [`QuasiNewtonPreconditioner`](@ref)
  * `sk`:                            現在のステップ
  * `yk`:                            現在の勾配の差
  * `retraction_method::AbstractRetractionMethod`: 使用する再traction $\operatorname{retr}$、[再tractionに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `stepsize::Stepsize`: [`Stepsize`](@ref) から継承されたファンクタで、ステップサイズを決定
  * `stop::StoppingCriterion`: 停止基準が満たされていることを示すファンクタ
  * `X::T`: マニフォールド $\mathcal M$ 上の点 $p$ での接ベクトルで、現在の反復での勾配を格納
  * `X_old`:                         最後の勾配

# コンストラクタ

```
QuasiNewtonState(M::AbstractManifold, p; kwargs...)
```

開始点 `p` でマニフォールド `M` 上に準ニュートン状態を生成します。

## キーワード引数

  * `direction_update=`[`QuasiNewtonLimitedMemoryDirectionUpdate`](@ref)`(M, p, InverseBFGS(), memory_size; vector_transport_method=vector_transport_method)`
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(1000)`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(1e-6)`: 停止基準が満たされていることを示すファンクタ
  * `initial_scale=1.0`: 相対的な初期スケール。デフォルトでは前処理器を使用する場合は無効化されます。
  * `memory_size=20`: デフォルトの方向更新でメモリを設定するためのショートカット
  * `preconditioner::Union{`[`QuasiNewtonPreconditioner`](@ref)`, Nothing} = nothing` 前処理器を指定するか、`nothing` を渡すことで無効化します。
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する再traction $\operatorname{retr}$、[再tractionに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `stepsize=`[`default_stepsize`](@ref)`(M, QuasiNewtonState)`: ステップサイズを決定するための [`Stepsize`](@ref) から継承されたファンクタ
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、[ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`)を参照
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: 接ベクトルの表現を指定するためのマニフォールド $\mathcal M$ 上の点 $p$ での接ベクトル

# 参照

[`quasi_Newton`](@ref)
