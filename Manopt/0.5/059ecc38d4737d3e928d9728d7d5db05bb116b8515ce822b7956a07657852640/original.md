```
projected_gradient_method(M, f, grad_f, proj, p=rand(M); kwargs...)
projected_gradient_method(M, obj::ManifoldConstrainedSetObjective, p=rand(M); kwargs...)
projected_gradient_method!(M, f, grad_f, proj, p; kwargs...)
projected_gradient_method!(M, obj::ManifoldConstrainedSetObjective, p; kwargs...)
```

Compute the projected gradient method for the constrained problem

$$
\begin{aligned}
\operatorname*{arg\,min}_{p ∈ \mathcal M} & f(p)\\
\text{subject to}\quad& p ∈ \mathcal C ⊂ \mathcal M
\end{aligned}
$$

by performing the following steps

1. Using the `stepsize` $α_k$ compute a candidate $q_k = \operatorname{proj}_{\mathcal C}\Bigl(\operatorname{retr}_{p_k}\bigl(-α_k \operatorname{grad} f(p_k)\bigr)\Bigr)$
2. Compute a backtracking stepsize $β_k ≤ 1$ along $Y_k = \operatorname{retr}_{p_k}^{-1}q_k$
3. Compute the new iterate $p_{k+1} = \operatorname{retr}_{p_k}( β_k \operatorname{retr}_{p_k}^{-1}q_k )$

until the `stopping_criterion=` is fulfilled.

For more information see [BergmannFerreiraNemethZhu:2025](@cite).

# Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `f`: a cost function $f: \mathcal M→ ℝ$ implemented as `(M, p) -> v`
  * `grad_f`: the (Riemannian) gradient $\operatorname{grad}f: \mathcal M → T_{p}\mathcal M$ of f as a function `(M, p) -> X` or a function `(M, X, p) -> X` computing `X` in-place
  * `proj` the function that projects onto the set $\mathcal C$ as a function `(M, p) -> q` or a function `(M, q, p) -> q` computing the projection in-place of `q`.
  * `p`: a point on the manifold $\mathcal M$

# Keyword arguments

  * `backtrack=`[`ArmijoLinesearchStepsize`](@ref)`(M; stop_increasing_at_step=0)`: a functor inheriting from [`Stepsize`](@ref) to determine a step size to perform the backtracking to determine the $β_k$. Note that the method requires $β_k ≤ 1$, otherwise the projection step no longer provides points within the constraints
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stepsize=`[`ConstantStepsize`](@ref)`(injectivity_radius(M)/2)`: a functor inheriting from [`Stepsize`](@ref) to determine a step size to perform the candidate projected step.
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(500)`[`|`](@ref StopWhenAny)``[`StopWhenGradientNormLess`](@ref)`(1.0e-6)`): a functor indicating that the stopping criterion is fulfilled

All other keyword arguments are passed to [`decorate_state!`](@ref) for state decorators or [`decorate_objective!`](@ref) for objective decorators, respectively.

# Output

The obtained approximate minimizer $p^*$. To obtain the whole final state of the solver, see [`get_solver_return`](@ref) for details, especially the `return_state=` keyword.
