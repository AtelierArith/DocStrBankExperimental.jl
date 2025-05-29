```
gradient_descent!(M, f, grad_f, p; kwargs...)
gradient_descent!(M, gradient_objective, p; kwargs...)
```

`p`の位置で勾配降下法を実行します。

$$
p_{k+1} = \operatorname{retr}_{p_k}\bigl( s_k\operatorname{grad}f(p_k) \bigr)
$$

異なる選択肢の$s_k$で`p`の位置で。

# 入力

  * `M`      多様体 $\mathcal M$
  * `f`      最小化するコスト関数 $F:\mathcal M→ℝ$
  * `grad_f` 関数Fの勾配 $\operatorname{grad}F:\mathcal M→ T\mathcal M$
  * `p`      初期値 $p ∈ \mathcal M$

`f`と`grad_f`の代わりに、[`AbstractManifoldGradientObjective`](@ref) `gradient_objective`を直接提供することもできます。

特に$s_k$のためのより多くのオプション、特に[`Stepsize`](@ref)については、[`gradient_descent`](@ref)を参照してください。
