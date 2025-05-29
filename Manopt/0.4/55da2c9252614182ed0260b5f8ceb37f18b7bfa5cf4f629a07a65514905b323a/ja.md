```
stochastic_gradient_descent(M, grad_f, p; kwargs...)
stochastic_gradient_descent(M, msgo, p; kwargs...)
```

確率的勾配降下法を実行します

# 入力

  * `M`:      多様体 $\mathcal M$
  * `grad_f`: 勾配関数で、サブ勾配のベクトルを返すか、勾配のベクトルである必要があります
  * `p`:      初期値 $x ∈ \mathcal M$

勾配の代わりに [`ManifoldStochasticGradientObjective`](@ref) `msgo` を提供することもでき、その場合 `cost=` キーワードは効果がありません。なぜなら、コストはすでに目的の中に含まれているからです。

# オプション

  * `cost`:               （`missing`）関数値を追跡するためのコスト関数を提供できます
  * `evaluation`:         （[`AllocatingEvaluation`](@ref)）勾配が割り当てによって動作するか（デフォルト）、`gradF(M, x)` の形で、または [`InplaceEvaluation`](@ref) の形で `gradF!(M, X, x)`（要素ごと）を指定します。
  * `evaluation_order`:   （`:Random`）ランダムに順序を入れ替えたシーケンス（`:FixedRandom`）、サイクルごとに順序を入れ替えたシーケンス（`:Linear`）、またはデフォルトの `:Random` を使用するかを指定します。
  * `stopping_criterion`: （[`StopAfterIteration`](@ref)`(1000)`) [`StoppingCriterion`](@ref)
  * `stepsize`:           （[`ConstantStepsize`](@ref)`(1.0)`) [`Stepsize`](@ref)
  * `order_type`:         （`:RandomOder`）勾配評価の順序のタイプ。可能な値は `:RandomOrder`、`：FixedPermutation`、`：LinearOrder` です。
  * `order`:              （`[1:n]`）初期の順列で、`n` は `gradF` の勾配の数です。
  * `retraction_method`:  （`default_retraction_method(M, typeof(p))`）使用するリトラクション。

# 出力

得られた（近似的な）最小化点 $p^*$、詳細については [`get_solver_return`](@ref) を参照してください。
