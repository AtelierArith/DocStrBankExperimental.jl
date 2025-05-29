```
gradient_descent(M, f, grad_f, p=rand(M); kwargs...)
gradient_descent(M, gradient_objective, p=rand(M); kwargs...)
```

perform a gradient descent

$$
p_{k+1} = \operatorname{retr}_{p_k}\bigl( s_k\operatorname{grad}f(p_k) \bigr),
\qquad k=0,1,…
$$

with different choices of the stepsize $s_k$ available (see `stepsize` option below).

# Input

  * `M`       a manifold $\mathcal M$
  * `f`       a cost function $f: \mathcal M→ℝ$ to find a minimizer $p^*$ for
  * `grad_f`  the gradient $\operatorname{grad}f: \mathcal M → T\mathcal M$ of f as a function `(M, p) -> X` or a function `(M, X, p) -> X`
  * `p`       an initial value `p` $= p_0 ∈ \mathcal M$

Alternatively to `f` and `grad_f` you can provide the [`AbstractManifoldGradientObjective`](@ref) `gradient_objective` directly.

# Optional

  * `direction`:          ([`IdentityUpdateRule`](@ref)) perform a processing of the direction, e.g.
  * `evaluation`:         ([`AllocatingEvaluation`](@ref)) specify whether the gradient works by allocation (default) form `grad_f(M, p)` or [`InplaceEvaluation`](@ref) in place of the form `grad_f!(M, X, p)`.
  * `retraction_method`:  ([`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`) a retraction to use
  * `stepsize`:           ([`default_stepsize`](@ref)`(M, GradientDescentState)`) a [`Stepsize`](@ref)
  * `stopping_criterion`: ([`StopAfterIteration`](@ref)`(200) |`[`StopWhenGradientNormLess`](@ref)`(1e-8)`) a functor inheriting from [`StoppingCriterion`](@ref) indicating when to stop.
  * `X`:                  ([`zero_vector(M,p)`]) provide memory and/or type of the gradient to use`

If you provide the [`ManifoldGradientObjective`](@ref) directly, `evaluation` is ignored.

All other keyword arguments are passed to [`decorate_state!`](@ref) for state decorators or [`decorate_objective!`](@ref) for objective, respectively. If you provide the [`ManifoldGradientObjective`](@ref) directly, these decorations can still be specified

# Output

the obtained (approximate) minimizer $p^*$. To obtain the whole final state of the solver, see [`get_solver_return`](@ref) for details
