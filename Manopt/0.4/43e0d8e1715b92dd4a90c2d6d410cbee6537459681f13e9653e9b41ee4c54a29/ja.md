```
stochastic_gradient_descent!(M, grad_f, p)
stochastic_gradient_descent!(M, msgo, p)
```

`p`の代わりに確率的勾配降下法を実行します。

# 入力

  * `M`:      多様体 $\mathcal M$
  * `grad_f`: 勾配関数で、サブ勾配のベクトルを返すか、勾配のベクトルである
  * `p`:      初期値 $p ∈ \mathcal M$

勾配の代わりに[`ManifoldStochasticGradientObjective`](@ref) `msgo`を提供することもでき、その場合、`cost=`キーワードは効果がありません。なぜなら、その場合、コストはすでに目的の中にあるからです。

すべてのオプションのパラメータについては、[`stochastic_gradient_descent`](@ref)を参照してください。
