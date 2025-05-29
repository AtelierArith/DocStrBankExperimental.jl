```
StochasticGradientDescentState <: AbstractGradientDescentSolverState
```

デフォルトの確率的勾配降下アルゴリズムのために次のフィールドを格納します。詳細は[`ManifoldStochasticGradientObjective`](@ref)および[`stochastic_gradient_descent`](@ref)を参照してください。

# フィールド

  * `p`:                  現在の反復点
  * `direction`:          ([`StochasticGradient`](@ref)) 使用する方向の更新
  * `stopping_criterion`: ([`StopAfterIteration`](@ref)`(1000)`) [`StoppingCriterion`](@ref)
  * `stepsize`:           ([`ConstantStepsize`](@ref)`(1.0)`) [`Stepsize`](@ref)
  * `evaluation_order`:   (`:Random`) ランダムに順序を入れ替えたシーケンス（`:FixedRandom`）、サイクルごとに順序を入れ替えたシーケンス（`:Linear`）、またはデフォルトの`:Random`を使用するかどうかを指定します。
  * `order`:              現在の順序
  * `retraction_method`:  (`default_retraction_method(M, typeof(p))`) 使用する`retraction(M, p, X)`。

# コンストラクタ

```
StochasticGradientDescentState(M, p)
```

開始点`p`で`StochasticGradientDescentState`を作成します。他のすべてのフィールドはオプションのキーワード引数であり、デフォルトは`M`から取得されます。
