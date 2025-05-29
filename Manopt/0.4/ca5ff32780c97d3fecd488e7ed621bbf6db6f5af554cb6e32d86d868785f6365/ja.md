```
conjugate_gradient_descent!(M, F, gradF, x)
conjugate_gradient_descent!(M, gradient_objective, p; kwargs...)
```

`x`の代わりに次のように共役勾配降下法を行います。

$$
p_{k+1} = \operatorname{retr}_{p_k} \bigl( s_k\delta_k \bigr),
$$

ここで、$\operatorname{retr}$は`Manifold` `M`上の再収束を示します。

# 入力

  * `M`:      多様体 $\mathcal M$
  * `f`:      最小化するコスト関数 $F:\mathcal M→ℝ$
  * `grad_f`: Fの勾配 $\operatorname{grad}F:\mathcal M→ T\mathcal M$
  * `p`:      初期値 $p∈\mathcal M$

`f`および`grad_f`の代わりに、[`AbstractManifoldGradientObjective`](@ref) `gradient_objective`を直接提供することもできます。

詳細やオプション、特に[`DirectionUpdateRule`](@ref)については、[`conjugate_gradient_descent`](@ref)を参照してください。
