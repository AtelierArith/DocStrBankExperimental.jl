```
AlternatingGradientDescentState <: AbstractGradientDescentSolverState
```

交互勾配降下アルゴリズムのフィールドを格納します。詳細は [`alternating_gradient_descent`](@ref) を参照してください。

# フィールド

  * `direction`:          (`AlternatingGradient(zero_vector(M, x))` [`DirectionUpdateRule`](@ref) の
  * `evaluation_order`:   (`:Linear`) ランダムに順序を入れ替えたシーケンス (`:FixedRandom`)、サイクルごとに新たに順序を入れ替えたシーケンス (`:Random`)、またはデフォルトの `:Linear` 評価順序を使用するかどうか。
  * `inner_iterations`:   (`5`) 次のコンポーネントに交互に移る前に、コンポーネント内で取る勾配ステップの数
  * `order` 現在の順列
  * `retraction_method`:  (`default_retraction_method(M, typeof(p))`) 使用する `retraction(M,x,ξ)`。
  * `stepsize`:           ([`ConstantStepsize`](@ref)`(M)`) [`Stepsize`](@ref)
  * `stopping_criterion`: ([`StopAfterIteration`](@ref)`(1000)`) [`StoppingCriterion`](@ref)
  * `p`:                  現在の反復点
  * `X`:                  (`zero_vector(M,p)`) 現在の勾配接線ベクトル
  * `k`, ì`:              外部および内部の反復のための内部カウンタ。

# コンストラクタ

```
AlternatingGradientDescentState(M, p; kwargs...)
```

点 `p` のオプションを生成し、`inner_iterations`、`order_type`、`order`、`retraction_method`、`stopping_criterion`、および `stepsize` がキーワード引数であることを示します。
