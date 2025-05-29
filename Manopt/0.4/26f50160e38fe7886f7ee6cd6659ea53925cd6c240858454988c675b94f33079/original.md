```
NelderMeadState <: AbstractManoptSolverState
```

Describes all parameters and the state of a Nelder-Mead heuristic based optimization algorithm.

# Fields

The naming of these parameters follows the [Wikipedia article](https://en.wikipedia.org/wiki/Nelder–Mead_method) of the Euclidean case. The default is given in brackets, the required value range after the description

  * `population`                an `Array{`point`,1}` of $n+1$ points $x_i$, $i=1,…,n+1$, where $n$ is the dimension of the manifold.
  * `stopping_criterion`:        ([`StopAfterIteration`](@ref)`(2000) |`[`StopWhenPopulationConcentrated`](@ref)`()`) a [`StoppingCriterion`](@ref)
  * `α`:                         (`1.`) reflection parameter ($α > 0$)
  * `γ`:                         (`2.`) expansion parameter ($γ > 0$)
  * `ρ`:                         (`1/2`) contraction parameter, $0 < ρ ≤ \frac{1}{2}$,
  * `σ`:                         (`1/2`) shrink coefficient, $0 < σ ≤ 1$
  * `p`:                         (`copy(population.pts[1])`) - a field to collect the current best value (initialized to *some* point here)
  * `retraction_method`:         (`default_retraction_method(M, typeof(p))`) the retraction to use.
  * `inverse_retraction_method`: (`default_inverse_retraction_method(M, typeof(p))`) an inverse retraction to use.

# Constructors

```
NelderMeadState(M[, population::NelderMeadSimplex]; kwargs...)
```

Construct a Nelder-Mead Option with a default population (if not provided) of set of `dimension(M)+1` random points stored in [`NelderMeadSimplex`](@ref).

In the constructor all fields (besides the population) are keyword arguments.
