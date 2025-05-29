```
gradient_descent(M, f, grad_f, p=rand(M); kwargs...)
gradient_descent(M, gradient_objective, p=rand(M); kwargs...)
gradient_descent!(M, f, grad_f, p; kwargs...)
gradient_descent!(M, gradient_objective, p; kwargs...)
```

perform the gradient descent algorithm

$$
p_{k+1} = \operatorname{retr}_{p_k}\bigl( s_k\operatorname{grad}f(p_k) \bigr),
\qquad k=0,1,…
$$

where $s_k > 0$ denotes a step size.

The algorithm can be performed in-place of `p`.

# Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `f`: a cost function $f: \mathcal M→ ℝ$ implemented as `(M, p) -> v`
  * `grad_f`: the (Riemannian) gradient $\operatorname{grad}f: \mathcal M → T_{p}\mathcal M$ of f as a function `(M, p) -> X` or a function `(M, X, p) -> X` computing `X` in-place
  * `p`: a point on the manifold $\mathcal M$

Alternatively to `f` and `grad_f` you can provide the corresponding [`AbstractManifoldGradientObjective`](@ref) `gradient_objective` directly.

# Keyword arguments

  * `direction=`[`IdentityUpdateRule`](@ref)`()`: specify to perform a certain processing of the direction, for example [`Nesterov`](@ref), [`MomentumGradient`](@ref) or [`AverageGradient`](@ref).
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.For example `grad_f(M,p)` allocates, but `grad_f!(M, X, p)` computes the result in-place of `X`.
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stepsize=`[`default_stepsize`](@ref)`(M, GradientDescentState)`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(200)`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(1e-8)`: a functor indicating that the stopping criterion is fulfilled
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: a tangent vector at the point $p$ on the manifold $\mathcal M$storing the gradient at the current iterate

All other keyword arguments are passed to [`decorate_state!`](@ref) for state decorators or [`decorate_objective!`](@ref) for objective decorators, respectively.

If you provide the [`ManifoldGradientObjective`](@ref) directly, the `evaluation=` keyword is ignored. The decorations are still applied to the objective.

If you activate tutorial mode (cf. [`is_tutorial_mode`](@ref)), this solver provides additional debug warnings.

# Output

The obtained approximate minimizer $p^*$. To obtain the whole final state of the solver, see [`get_solver_return`](@ref) for details, especially the `return_state=` keyword.
