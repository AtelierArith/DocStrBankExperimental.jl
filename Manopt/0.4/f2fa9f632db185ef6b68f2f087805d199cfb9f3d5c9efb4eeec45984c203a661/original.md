```
subgradient_method(M, f, ∂f, p=rand(M); kwargs...)
subgradient_method(M, sgo, p=rand(M); kwargs...)
```

perform a subgradient method $p_{k+1} = \mathrm{retr}(p_k, s_k∂f(p_k))$,

where $\mathrm{retr}$ is a retraction, $s_k$ is a step size, usually the [`ConstantStepsize`](@ref) but also be specified. Though the subgradient might be set valued, the argument `∂f` should always return *one* element from the subgradient, but not necessarily deterministic. For more details see [FerreiraOliveira:1998](@cite).

# Input

  * `M`:  a manifold $\mathcal M$
  * `f`:  a cost function $f:\mathcal M→ℝ$ to minimize
  * `∂f`: the (sub)gradient $∂ f: \mathcal M→ T\mathcal M$ of f restricted to always only returning one value/element from the subdifferential. This function can be passed as an allocation function `(M, p) -> X` or a mutating function `(M, X, p) -> X`, see `evaluation`.
  * `p`:  (`rand(M)`) an initial value $p_0=p ∈ \mathcal M$

alternatively to `f` and `∂f` a [`ManifoldSubgradientObjective`](@ref) `sgo` can be provided.

# Optional

  * `evaluation`:         ([`AllocatingEvaluation`](@ref)) specify whether the subgradient works by allocation (default) form `∂f(M, y)` or [`InplaceEvaluation`](@ref) in place of the form `∂f!(M, X, x)`.
  * `retraction`:         (`default_retraction_method(M, typeof(p))`) a retraction to use.
  * `stepsize`:           ([`ConstantStepsize`](@ref)`(M)`) specify a [`Stepsize`](@ref)
  * `stopping_criterion`: ([`StopAfterIteration`](@ref)`(5000)`) a functor, see[`StoppingCriterion`](@ref), indicating when to stop.

and the ones that are passed to [`decorate_state!`](@ref) for decorators.

# Output

the obtained (approximate) minimizer $p^*$, see [`get_solver_return`](@ref) for details
