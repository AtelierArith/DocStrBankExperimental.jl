```
NelderMeadState <: AbstractManoptSolverState
```

Describes all parameters and the state of a Nelder-Mead heuristic based optimization algorithm.

# Fields

The naming of these parameters follows the [Wikipedia article](https://en.wikipedia.org/wiki/Nelder–Mead_method) of the Euclidean case. The default is given in brackets, the required value range after the description

  * `population::`[`NelderMeadSimplex`](@ref): a population (set) of $d+1$ points $x_i$, $i=1,…,n+1$, where $d$ is the [`manifold_dimension`](@extref `ManifoldsBase.manifold_dimension-Tuple{AbstractManifold}`) of `M`.
  * `stepsize::Stepsize`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `α`: the reflection parameter $α > 0$:
  * `γ` the expansion parameter $γ > 0$:
  * `ρ`: the contraction parameter, $0 < ρ ≤ \frac{1}{2}$,
  * `σ`: the shrinkage coefficient, $0 < σ ≤ 1$
  * `p::P`: a point on the manifold $\mathcal M$ storing the current best point
  * `inverse_retraction_method::AbstractInverseRetractionMethod`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `retraction_method::AbstractRetractionMethod`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)

# Constructors

```
NelderMeadState(M::AbstractManifold; kwargs...)
```

Construct a Nelder-Mead Option with a default population (if not provided) of set of `dimension(M)+1` random points stored in [`NelderMeadSimplex`](@ref).

# Keyword arguments

  * `population=`[`NelderMeadSimplex`](@ref)`(M)`
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(2000)`[`|`](@ref StopWhenAny)[`StopWhenPopulationConcentrated`](@ref)`()`): a functor indicating that the stopping criterion is fulfilled a [`StoppingCriterion`](@ref)
  * `α=1.0`: reflection parameter $α > 0$:
  * `γ=2.0` expansion parameter $γ$:
  * `ρ=1/2`: contraction parameter, $0 < ρ ≤ \frac{1}{2}$,
  * `σ=1/2`: shrink coefficient, $0 < σ ≤ 1$
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `p=copy(M, population.pts[1])`: initialise the storage for the best point (iterate)¨
