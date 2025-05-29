```
subgradient_method(M, f, ∂f, p=rand(M); kwargs...)
subgradient_method(M, sgo, p=rand(M); kwargs...)
subgradient_method!(M, f, ∂f, p; kwargs...)
subgradient_method!(M, sgo, p; kwargs...)
```

perform a subgradient method $p^{(k+1)} = \operatorname{retr}\bigl(p^{(k)}, s^{(k)}∂f(p^{(k)})\bigr)$, where $\operatorname{retr}$ is a retraction, $s^{(k)}$ is a step size.

Though the subgradient might be set valued, the argument `∂f` should always return *one* element from the subgradient, but not necessarily deterministic. For more details see [FerreiraOliveira:1998](@cite).

# Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `f`: a cost function $f: \mathcal M→ ℝ$ implemented as `(M, p) -> v`
  * `∂f`: the (sub)gradient $∂ f: \mathcal M → T\mathcal M$ of f
  * `p`: a point on the manifold $\mathcal M$

alternatively to `f` and `∂f` a [`ManifoldSubgradientObjective`](@ref) `sgo` can be provided.

# Keyword arguments

  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stepsize=`[`default_stepsize`](@ref)`(M, SubGradientMethodState)`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(5000)`: a functor indicating that the stopping criterion is fulfilled
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: a tangent vector at the point $p$ on the manifold $\mathcal M$to specify the representation of a tangent vector

and the ones that are passed to [`decorate_state!`](@ref) for decorators.

# Output

the obtained (approximate) minimizer $p^*$, see [`get_solver_return`](@ref) for details
