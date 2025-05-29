```
ProjectedGradientMethodState <: AbstractManoptSolverState
```

# フィールド

  * `backtracking::Stepsize`: ステップサイズ $β_k$ を決定するための [`Stepsize`](@ref) から継承されたファンクタ
  * `inverse_retraction_method::AbstractInverseRetractionMethod`: 使用する逆再収縮 $\operatorname{retr}^{-1}$、[再収縮とその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `p::P`: 現在の反復を格納する多様体 $\mathcal M$ 上の点
  * `q`: 投影勾配ステップのための中間点
  * `stepsize::Stepsize`: 候補 $q_k$ を決定するためのステップサイズ $α_k$ を決定するための [`Stepsize`](@ref) から継承されたファンクタ
  * `stop::StoppingCriterion`: 停止基準が満たされていることを示すファンクタ
  * `retraction_method::AbstractRetractionMethod`: 使用する再収縮 $\operatorname{retr}$、[再収縮に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `X::T`: 多様体 $\mathcal M$ 上の点 $p$ での接ベクトル
  * `Y::T`: バックトラッキング内で使用される接ベクトルを格納するための一時メモリ

# コンストラクタ

```
ProjectedGradientMethodState(M, p=rand(M); kwargs...)
```

## キーワード引数

  * `backtracking=`[`ArmijoLinesearchStepsize`](@ref)`(M)`: 候補 $q_k$ へのステップサイズ $p_k$ を決定するための [`Stepsize`](@ref) から継承されたファンクタ
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する逆再収縮 $\operatorname{retr}^{-1}$、[再収縮とその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `stepsize=`[`ConstantStepsize`](@ref)`(M)`: 候補 $q_k$ を決定するためのステップサイズ $α_k$ を決定するための [`Stepsize`](@ref) から継承されたファンクタ
  * `stop=`[`StopAfterIteration`](@ref)`(300)`: 停止基準が満たされていることを示すファンクタ
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する再収縮 $\operatorname{retr}$、[再収縮に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: 多様体 $\mathcal M$ 上の点 $p$ での接ベクトル
