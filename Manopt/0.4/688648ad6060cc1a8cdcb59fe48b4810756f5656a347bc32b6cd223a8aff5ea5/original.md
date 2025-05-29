```
cyclic_proximal_point(M, f, proxes_f, p)
cyclic_proximal_point(M, mpo, p)
```

perform a cyclic proximal point algorithm.

# Input

  * `M`:        a manifold $\mathcal M$
  * `f`:        a cost function $f:\mathcal M→ℝ$ to minimize
  * `proxes_f`: an Array of proximal maps (`Function`s) `(M,λ,p) -> q` or `(M, q, λ, p) -> q` for the summands of $f$ (see `evaluation`)
  * `p`:        an initial value $p ∈ \mathcal M$

where `f` and the proximal maps `proxes_f` can also be given directly as a [`ManifoldProximalMapObjective`](@ref) `mpo`

# Optional

  * `evaluation`:         ([`AllocatingEvaluation`](@ref)) specify whether the proximal maps work by allocation (default) form `prox(M, λ, x)` or [`InplaceEvaluation`](@ref) in place of form `prox!(M, y, λ, x)`.
  * `evaluation_order`:   (`:Linear`) whether to use a randomly permuted sequence (`:FixedRandom`), a per cycle permuted sequence (`:Random`) or the default linear one.
  * `λ`:                  (`iter -> 1/iter` ) a function returning the (square summable but not summable) sequence of $λ_i$
  * `stopping_criterion`: ([`StopAfterIteration`](@ref)`(5000) |`[`StopWhenChangeLess`](@ref)`(1e-12)`) a [`StoppingCriterion`](@ref).

All other keyword arguments are passed to [`decorate_state!`](@ref) for decorators or [`decorate_objective!`](@ref), respectively. If you provide the [`ManifoldProximalMapObjective`](@ref) directly, these decorations can still be specified.

# Output

the obtained (approximate) minimizer $p^*$, see [`get_solver_return`](@ref) for details
