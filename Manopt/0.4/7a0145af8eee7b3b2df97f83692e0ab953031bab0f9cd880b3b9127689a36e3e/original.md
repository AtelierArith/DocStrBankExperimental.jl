```
NelderMead(M::AbstractManifold, f)
NelderMead(M::AbstractManifold, f, population::NelderMeadSimplex)
NelderMead(M::AbstractManifold, mco::AbstractManifoldCostObjective)
NelderMead(M::AbstractManifold, mco::AbstractManifoldCostObjective, population::NelderMeadSimplex)
```

Solve a Nelder-Mead minimization problem for the cost function $f:  \mathcal M$ on the manifold `M`. If the initial population `p` is not given, a random set of points is chosen.

This algorithm is adapted from the Euclidean Nelder-Mead method, see [https://en.wikipedia.org/wiki/Nelder-Mead_method](https://en.wikipedia.org/wiki/Nelder-Mead_method) and [http://www.optimization-online.org/DB_FILE/2007/08/1742.pdf](http://www.optimization-online.org/DB_FILE/2007/08/1742.pdf).

# Input

  * `M`:            a manifold $\mathcal M$
  * `f`:            a cost function to minimize
  * `population`:   ($n+1$ `rand(M)`s) an initial population of $n+1$ points, where $n$ is the dimension of the manifold `M`.

# Optional

  * `stopping_criterion`:        ([`StopAfterIteration`](@ref)`(2000) |`[`StopWhenPopulationConcentrated`](@ref)`()`) a [`StoppingCriterion`](@ref)
  * `α`:                         (`1.`) reflection parameter ($α > 0$)
  * `γ`:                         (`2.`) expansion parameter ($γ$)
  * `ρ`:                         (`1/2`) contraction parameter, $0 < ρ ≤ \frac{1}{2}$,
  * `σ`:                         (`1/2`) shrink coefficient, $0 < σ ≤ 1$
  * `retraction_method`:         (`default_retraction_method(M, typeof(p))`) the retraction to use
  * `inverse_retraction_method`: (`default_inverse_retraction_method(M, typeof(p))`) an inverse retraction to use.

and the ones that are passed to [`decorate_state!`](@ref) for decorators.

!!! note
    The manifold `M` used here has to either provide a `mean(M, pts)` or you have to load `Manifolds.jl` to use its statistics part.


# Output

the obtained (approximate) minimizer $p^*$, see [`get_solver_return`](@ref) for details
