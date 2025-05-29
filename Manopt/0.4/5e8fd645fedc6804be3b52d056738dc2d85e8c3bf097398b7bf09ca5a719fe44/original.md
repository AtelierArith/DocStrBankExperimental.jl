```
gradient_descent!(M, f, grad_f, p; kwargs...)
gradient_descent!(M, gradient_objective, p; kwargs...)
```

perform a Gradient descent in-place of `p`

$$
p_{k+1} = \operatorname{retr}_{p_k}\bigl( s_k\operatorname{grad}f(p_k) \bigr)
$$

in place of `p` with different choices of $s_k$ available.

# Input

  * `M`      a manifold $\mathcal M$
  * `f`      a cost function $F:\mathcal M→ℝ$ to minimize
  * `grad_f` the gradient $\operatorname{grad}F:\mathcal M→ T\mathcal M$ of F
  * `p`      an initial value $p ∈ \mathcal M$

Alternatively to `f` and `grad_f` you can provide the [`AbstractManifoldGradientObjective`](@ref) `gradient_objective` directly.

For more options, especially [`Stepsize`](@ref)s for $s_k$, see [`gradient_descent`](@ref)
