```
proximal_point(M, prox_f, p=rand(M); kwargs...)
proximal_point(M, mpmo, p=rand(M); kwargs...)
proximal_point!(M, prox_f, p; kwargs...)
proximal_point!(M, mpmo, p; kwargs...)
```

Perform the proximal point algoritm from [FerreiraOliveira:2002](@cite) which reads

$$
p^{(k+1)} = \operatorname{prox}_{λ_kf}(p^{(k)})
$$

# Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `prox_f`: a proximal map `(M,λ,p) -> q` or `(M, q, λ, p) -> q` for the summands of $f$ (see `evaluation`)

# Keyword arguments

  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.
  * `f=nothing`: a cost function $f: \mathcal M→ℝ$ to minimize. For running the algorithm, $f$ is not required, but for example when recording the cost or using a stopping criterion that requires a cost function.
  * `λ= k -> 1.0`: a function returning the (square summable but not summable) sequence of $λ_i$
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(200)`[`|`](@ref StopWhenAny)[`StopWhenChangeLess`](@ref)`(1e-12)`): a functor indicating that the stopping criterion is fulfilled

All other keyword arguments are passed to [`decorate_state!`](@ref) for state decorators or [`decorate_objective!`](@ref) for objective decorators, respectively.

# Output

The obtained approximate minimizer $p^*$. To obtain the whole final state of the solver, see [`get_solver_return`](@ref) for details, especially the `return_state=` keyword.
