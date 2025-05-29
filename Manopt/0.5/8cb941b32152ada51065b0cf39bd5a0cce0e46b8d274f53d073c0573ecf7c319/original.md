```
cyclic_proximal_point(M, f, proxes_f, p; kwargs...)
cyclic_proximal_point(M, mpo, p; kwargs...)
cyclic_proximal_point!(M, f, proxes_f; kwargs...)
cyclic_proximal_point!(M, mpo; kwargs...)
```

perform a cyclic proximal point algorithm. This can be done in-place of `p`.

# Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `f`:        a cost function $f: \mathcal M→ℝ$ to minimize
  * `proxes_f`: an Array of proximal maps (`Function`s) `(M,λ,p) -> q` or `(M, q, λ, p) -> q` for the summands of $f$ (see `evaluation`)

where `f` and the proximal maps `proxes_f` can also be given directly as a [`ManifoldProximalMapObjective`](@ref) `mpo`

# Keyword arguments

  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.
  * `evaluation_order=:Linear`: whether to use a randomly permuted sequence (`:FixedRandom`:, a per cycle permuted sequence (`:Random`) or the default linear one.
  * `λ=iter -> 1/iter`:         a function returning the (square summable but not summable) sequence of $λ_i$
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(5000)`[`|`](@ref StopWhenAny)[`StopWhenChangeLess`](@ref)`(1e-12)`): a functor indicating that the stopping criterion is fulfilled

All other keyword arguments are passed to [`decorate_state!`](@ref) for state decorators or [`decorate_objective!`](@ref) for objective decorators, respectively.

# Output

The obtained approximate minimizer $p^*$. To obtain the whole final state of the solver, see [`get_solver_return`](@ref) for details, especially the `return_state=` keyword.
