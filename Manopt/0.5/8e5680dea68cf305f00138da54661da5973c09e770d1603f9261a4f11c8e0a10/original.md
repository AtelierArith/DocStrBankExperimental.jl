```
conjugate_gradient_descent(M, f, grad_f, p=rand(M))
conjugate_gradient_descent!(M, f, grad_f, p)
conjugate_gradient_descent(M, gradient_objective, p)
conjugate_gradient_descent!(M, gradient_objective, p; kwargs...)
```

perform a conjugate gradient based descent-

$$
p_{k+1} = \operatorname{retr}_{p_k} \bigl( s_kδ_k \bigr),
$$

where $\operatorname{retr}$ denotes a retraction on the `Manifold` `M` and one can employ different rules to update the descent direction $δ_k$ based on the last direction $δ_{k-1}$ and both gradients $\operatorname{grad}f(x_k)$,$\operatorname{grad} f(x_{k-1})$. The [`Stepsize`](@ref) $s_k$ may be determined by a [`Linesearch`](@ref).

Alternatively to `f` and `grad_f` you can provide the [`AbstractManifoldGradientObjective`](@ref) `gradient_objective` directly.

Available update rules are [`SteepestDescentCoefficientRule`](@ref), which yields a [`gradient_descent`](@ref), [`ConjugateDescentCoefficient`](@ref) (the default), [`DaiYuanCoefficientRule`](@ref), [`FletcherReevesCoefficient`](@ref), [`HagerZhangCoefficient`](@ref), [`HestenesStiefelCoefficient`](@ref), [`LiuStoreyCoefficient`](@ref), and [`PolakRibiereCoefficient`](@ref). These can all be combined with a [`ConjugateGradientBealeRestartRule`](@ref) rule.

They all compute $β_k$ such that this algorithm updates the search direction as

$$
δ_k=\operatorname{grad}f(p_k) + β_k \delta_{k-1}
$$

# Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `f`: a cost function $f: \mathcal M→ ℝ$ implemented as `(M, p) -> v`
  * `grad_f`: the (Riemannian) gradient $\operatorname{grad}f: \mathcal M → T_{p}\mathcal M$ of f as a function `(M, p) -> X` or a function `(M, X, p) -> X` computing `X` in-place
  * `p`: a point on the manifold $\mathcal M$

# Keyword arguments

  * `coefficient::DirectionUpdateRule=`[`ConjugateDescentCoefficient`](@ref)`()`: rule to compute the descent direction update coefficient $β_k$, as a functor, where the resulting function maps are `(amp, cgs, k) -> β` with `amp` an [`AbstractManoptProblem`](@ref), `cgs` is the [`ConjugateGradientDescentState`](@ref), and `k` is the current iterate.
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stepsize=`[`ArmijoLinesearch`](@ref)`()`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(500)`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(1e-8)`: a functor indicating that the stopping criterion is fulfilled
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)

If you provide the [`ManifoldGradientObjective`](@ref) directly, the `evaluation=` keyword is ignored. The decorations are still applied to the objective.

# Output

The obtained approximate minimizer $p^*$. To obtain the whole final state of the solver, see [`get_solver_return`](@ref) for details, especially the `return_state=` keyword.
