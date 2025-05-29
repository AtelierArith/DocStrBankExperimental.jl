```
StochasticGradientDescentState <: AbstractGradientDescentSolverState
```

デフォルトの確率的勾配降下アルゴリズムのためのフィールドを以下に保存します。詳細は[`ManifoldStochasticGradientObjective`](@ref)および[`stochastic_gradient_descent`](@ref)を参照してください。

# フィールド

  * `p::P`: 現在の反復を格納する多様体 $\mathcal M$ 上の点
  * `direction`: 使用する方向の更新
  * `stop::StoppingCriterion`: 停止基準が満たされていることを示すファンクタ
  * `stepsize::Stepsize`: ステップサイズを決定するための[`Stepsize`](@ref)から継承したファンクタ
  * `evaluation_order`: ランダムに順序を入れ替えたシーケンス（`:FixedRandom`）、サイクルごとに順序を入れ替えたシーケンス（`:Linear`）、またはデフォルトの`:Random`シーケンスを使用するかを指定します。
  * `order`: 現在の順序を格納
  * `retraction_method::AbstractRetractionMethod`: 使用する再traction $\operatorname{retr}$、再tractionに関するセクションを参照してください[@extref ManifoldsBase :doc:`retractions`]

# コンストラクタ

```
StochasticGradientDescentState(M::AbstractManifold; kwargs...)
```

開始点 `p` で `StochasticGradientDescentState` を作成します。

# キーワード引数

  * `direction=`[`StochasticGradientRule`](@ref)`(M, [`zero*vector`](@extref`ManifoldsBase.zero*vector-Tuple{AbstractManifold, Any}`)`(M, p)`)
  * `order_type=:RandomOrder``
  * `order=Int[]`: 次のエポックのインデックスの順序をどのように保存するかを指定
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する再traction $\operatorname{retr}$、再tractionに関するセクションを参照してください[@extref ManifoldsBase :doc:`retractions`]
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: 初期値を指定するための多様体 $\mathcal M$ 上の点
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(1000)`: 停止基準が満たされていることを示すファンクタ
  * `stepsize=`[`default_stepsize`](@ref)`(M, StochasticGradientDescentState)`: ステップサイズを決定するための[`Stepsize`](@ref)から継承したファンクタ
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: 多様体 $\mathcal M$ 上の点 $p$ における接ベクトルを指定するための接ベクトルの表現
