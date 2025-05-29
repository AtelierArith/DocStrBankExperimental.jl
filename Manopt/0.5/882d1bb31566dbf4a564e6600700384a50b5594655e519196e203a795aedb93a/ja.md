```
GradientDescentState{P,T} <: AbstractGradientSolverState
```

勾配降下アルゴリズムの状態を説明します。

# フィールド

  * `p::P`: 現在の反復を格納する多様体 $\mathcal M$ 上の点
  * `X::T`: 現在の反復における勾配を格納する多様体 $\mathcal M$ 上の点 $p$ における接ベクトル
  * `stop::StoppingCriterion`: 停止基準が満たされたことを示すファンクタ
  * `stepsize::Stepsize`: ステップサイズを決定するための [`Stepsize`](@ref) から継承されたファンクタ
  * `direction::`[`DirectionUpdateRule`](@ref) : 取得した勾配を処理し、「歩く」方向を計算するプロセッサ。
  * `retraction_method::AbstractRetractionMethod`: 使用する再traction $\operatorname{retr}$、[再tractionに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照

# コンストラクタ

```
GradientDescentState(M::AbstractManifold; kwargs...)
```

勾配降下ソルバーの状態を初期化します。ここで

## 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$

## キーワード引数

  * `direction=`[`IdentityUpdateRule`](@ref)`()`
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: 初期値を指定するための多様体 $\mathcal M$ 上の点
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(100)`: 停止基準が満たされたことを示すファンクタ
  * `stepsize=`[`default_stepsize`](@ref)`(M, GradientDescentState; retraction_method=retraction_method)`: ステップサイズを決定するための [`Stepsize`](@ref) から継承されたファンクタ
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する再traction $\operatorname{retr}$、[再tractionに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: 接ベクトルの表現を指定するための多様体 $\mathcal M$ 上の点 $p$ における接ベクトル

# 参照

[`gradient_descent`](@ref)
