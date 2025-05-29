```
PrimalDualSemismoothNewtonState <: AbstractPrimalDualSolverState
```

# フィールド

  * `m::P`: 多様体 $\mathcal M$ 上の点
  * `n::Q`: 多様体 $\mathcal N$ 上の点
  * `p::P`: 現在の反復を格納する多様体 $\mathcal M$ 上の点
  * `X::T`: 多様体 $\mathcal M$ 上の点 $p$ での接ベクトル
  * `primal_stepsize::Float64`: プライマル近接の近接パラメータ
  * `dual_stepsize::Float64`: デュアル近接の近接パラメータ
  * `reg_param::Float64`: ニュートン行列の正則化パラメータ
  * `stop::StoppingCriterion`: 停止基準が満たされていることを示すファンクタ
  * `update_primal_base`: プライマルベースを更新する関数
  * `update_dual_base`: デュアルベースを更新する関数
  * `inverse_retraction_method::AbstractInverseRetractionMethod`: 使用する逆引き戻し $\operatorname{retr}^{-1}$、詳細は [引き戻しとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`) を参照
  * `retraction_method::AbstractRetractionMethod`: 使用する引き戻し $\operatorname{retr}$、詳細は [引き戻しに関するセクション](@extref ManifoldsBase :doc:`retractions`) を参照
  * `vector_transport_method::AbstractVectorTransportMethodP`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、詳細は [ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`) を参照

更新関数の引数としては、[`AbstractManoptProblem`](@ref) `amp`、[`AbstractManoptSolverState`](@ref) `ams`、および現在の反復 `i` があります。これらをデフォルトの恒等式とは異なるように有効にする場合、アルゴリズムが機能するために `p.Λ` を提供する必要があります（これは `missing` である可能性があります）。

# コンストラクタ

```
PrimalDualSemismoothNewtonState(M::AbstractManifold; kwargs...)
```

[`primal_dual_semismooth_Newton`](@ref) の状態を生成します。

## キーワード引数

  * `m=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`
  * `n=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(N)`
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`
  * `primal_stepsize=1/sqrt(8)`
  * `dual_stepsize=1/sqrt(8)`
  * `reg_param=1e-5`
  * `update_primal_base=(amp, ams, k) -> o.m`
  * `update_dual_base=(amp, ams, k) -> o.n`
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する引き戻し $\operatorname{retr}$、詳細は [引き戻しに関するセクション](@extref ManifoldsBase :doc:`retractions`) を参照
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する逆引き戻し $\operatorname{retr}^{-1}$、詳細は [引き戻しとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`) を参照
  * `stopping_criterion=``[`StopAfterIteration`](@ref)`(50)`: 停止基準が満たされていることを示すファンクタ
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、詳細は [ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`) を参照
