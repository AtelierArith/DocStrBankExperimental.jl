```
conjugate_gradient_descent(M, F, gradF, p=rand(M))
conjugate_gradient_descent(M, gradient_objective, p)
```

perform a conjugate gradient based descent

$$
p_{k+1} = \operatorname{retr}_{p_k} \bigl( s_kδ_k \bigr),
$$

where $\operatorname{retr}$ denotes a retraction on the `Manifold` `M` and one can employ different rules to update the descent direction $δ_k$ based on the last direction $δ_{k-1}$ and both gradients $\operatorname{grad}f(x_k)$,$\operatorname{grad}f(x_{k-1})$. The [`Stepsize`](@ref) $s_k$ may be determined by a [`Linesearch`](@ref).

Alternatively to `f` and `grad_f` you can provide the [`AbstractManifoldGradientObjective`](@ref) `gradient_objective` directly.

Available update rules are [`SteepestDirectionUpdateRule`](@ref), which yields a [`gradient_descent`](@ref), [`ConjugateDescentCoefficient`](@ref) (the default), [`DaiYuanCoefficient`](@ref), [`FletcherReevesCoefficient`](@ref), [`HagerZhangCoefficient`](@ref), [`HestenesStiefelCoefficient`](@ref), [`LiuStoreyCoefficient`](@ref), and [`PolakRibiereCoefficient`](@ref). These can all be combined with a [`ConjugateGradientBealeRestart`](@ref) rule.

They all compute $β_k$ such that this algorithm updates the search direction as

$$
\delta_k=\operatorname{grad}f(p_k) + β_k \delta_{k-1}
$$

# Input

  * `M`      a manifold $\mathcal M$
  * `f`      a cost function $F:\mathcal M→ℝ$ to minimize implemented as a function `(M,p) -> v`
  * `grad_f` the gradient $\operatorname{grad}F:\mathcal M → T\mathcal M$ of $F$ implemented also as `(M,x) -> X`
  * `p`      an initial value $x∈\mathcal M$

# Optional

  * `coefficient`:             ([`ConjugateDescentCoefficient`](@ref) `<:` [`DirectionUpdateRule`](@ref)) rule to compute the descent direction update coefficient $β_k$, as a functor, where the resulting function maps are `(amp, cgs, i) -> β` with `amp` an [`AbstractManoptProblem`](@ref), `cgs` is the [`ConjugateGradientDescentState`](@ref), and `i` is the current iterate.
  * `evaluation`:              ([`AllocatingEvaluation`](@ref)) specify whether the gradient works by allocation (default) form `gradF(M, x)` or [`InplaceEvaluation`](@ref) in place of the form `gradF!(M, X, x)`.
  * `retraction_method`: (`default_retraction_method(M, typeof(p))`) a retraction method to use.
  * `stepsize`:                ([`ArmijoLinesearch`](@ref) via [`default_stepsize`](@ref)) A [`Stepsize`](@ref) function applied to the search direction. The default is a constant step size 1.
  * `stopping_criterion`:      (`stopWhenAny( stopAtIteration(200), stopGradientNormLess(10.0^-8))`) a function indicating when to stop.
  * `vector_transport_method`: (`default_vector_transport_method(M, typeof(p))`) vector transport method to transport the old descent direction when computing the new descent direction.

If you provide the [`ManifoldGradientObjective`](@ref) directly, `evaluation` is ignored.

# Output

the obtained (approximate) minimizer $p^*$, see [`get_solver_return`](@ref) for details
