```
AlternatingGradientDescentState <: AbstractGradientDescentSolverState
```

交互勾配降下アルゴリズムのフィールドを格納します。詳細は[`alternating_gradient_descent`](@ref)を参照してください。

# フィールド

  * `direction::`[`DirectionUpdateRule`](@ref)
  * `evaluation_order::Symbol`: ランダムに順序を入れ替えたシーケンス（`:FixedRandom`）、サイクルごとに新たに入れ替えたシーケンス（`:Random`）、またはデフォルトの`:Linear`評価順序を使用するかどうか。
  * `inner_iterations`: 次のコンポーネントに交互に移る前に取る勾配ステップの数
  * `order`: 現在の順列
  * `retraction_method::AbstractRetractionMethod`: 使用するリトラクション $\operatorname{retr}$、リトラクションに関するセクションを参照してください [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stepsize::Stepsize`: ステップサイズを決定するための[`Stepsize`](@ref)から継承されたファンクタ
  * `stop::StoppingCriterion`: 停止基準が満たされていることを示すファンクタ
  * `p::P`: 現在の反復を格納する多様体 $\mathcal M$ 上の点
  * `X::T`: 現在の反復における勾配を格納する多様体 $\mathcal M$ 上の点 $p$ における接ベクトル
  * `k`, `ì`: 外部および内部反復のための内部カウンタ。

# コンストラクタ

```
AlternatingGradientDescentState(M::AbstractManifold; kwargs...)
```

# キーワード引数

  * `inner_iterations=5`
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: 多様体 $\mathcal M$ 上の点
  * `order_type::Symbol=:Linear`
  * `order::Vector{<:Int}=Int[]`
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(1000)`: 停止基準が満たされていることを示すファンクタ
  * `stepsize=`[`default_stepsize`](@ref)`(M, AlternatingGradientDescentState)`: ステップサイズを決定するための[`Stepsize`](@ref)から継承されたファンクタ
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: 多様体 $\mathcal M$ 上の点 $p$ における接ベクトル

点 `p` のオプションを生成し、`inner_iterations`、`order_type`、`order`、`retraction_method`、`stopping_criterion`、および `stepsize` がキーワード引数であることを確認します。
