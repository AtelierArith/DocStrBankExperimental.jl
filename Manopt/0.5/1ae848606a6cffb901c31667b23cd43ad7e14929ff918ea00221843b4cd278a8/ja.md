```
SubGradientMethodState <: AbstractManoptSolverState
```

は [`subgradient_method`](@ref) ソルバーのオプション値を格納します。

# フィールド

  * `p::P`: 現在の反復を格納する多様体 $\mathcal M$ 上の点
  * `p_star`: 最適値
  * `retraction_method::AbstractRetractionMethod`: 使用する再traction $\operatorname{retr}$、[再tractionに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `stepsize::Stepsize`: ステップサイズを決定するための [`Stepsize`](@ref) から継承されたファンクタ
  * `stop::StoppingCriterion`: 停止基準が満たされていることを示すファンクタ
  * `X`: 最後に評価された点 `p` における可能なサブ勾配の現在の要素。

# コンストラクタ

```
SubGradientMethodState(M::AbstractManifold; kwargs...)
```

サブグラディエント法の状態を初期化します。

# キーワード引数

  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する再traction $\operatorname{retr}$、[再tractionに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: 初期値を指定するための多様体 $\mathcal M$ 上の点
  * `stepsize=`[`default_stepsize`](@ref)`(M, SubGradientMethodState)`: ステップサイズを決定するための [`Stepsize`](@ref) から継承されたファンクタ
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(5000)`: 停止基準が満たされていることを示すファンクタ
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: 接ベクトルの表現を指定するための多様体 $\mathcal M$ 上の点 $p$ における接ベクトル
