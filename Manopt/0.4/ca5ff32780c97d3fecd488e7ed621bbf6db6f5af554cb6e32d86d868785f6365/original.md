```
conjugate_gradient_descent!(M, F, gradF, x)
conjugate_gradient_descent!(M, gradient_objective, p; kwargs...)
```

perform a conjugate gradient based descent in place of `x` as

$$
p_{k+1} = \operatorname{retr}_{p_k} \bigl( s_k\delta_k \bigr),
$$

where $\operatorname{retr}$ denotes a retraction on the `Manifold` `M`

# Input

  * `M`:      a manifold $\mathcal M$
  * `f`:      a cost function $F:\mathcal M→ℝ$ to minimize
  * `grad_f`: the gradient $\operatorname{grad}F:\mathcal M→ T\mathcal M$ of F
  * `p`:      an initial value $p∈\mathcal M$

Alternatively to `f` and `grad_f` you can provide the [`AbstractManifoldGradientObjective`](@ref) `gradient_objective` directly.

for more details and options, especially the [`DirectionUpdateRule`](@ref)s, see [`conjugate_gradient_descent`](@ref).
