Implementation of Evolution Strategy: (μ/ρ(+/,)λ)-ES

The constructor takes following keyword arguments:

  * `initStrategy`: an initial strategy description, (default: empty)
  * `recombination`: ES recombination function for population (default: `first`), see [Crossover](@ref)
  * `srecombination`: ES recombination function for strategies (default: `first`), see [Crossover](@ref)
  * `mutation`: [Mutation](@ref) function for population (default: [`nop`](@ref))
  * `smutation`: [Mutation](@ref) function for strategies (default: [`nop`](@ref))
  * `μ`/`mu`: the number of parents
  * `ρ`/`rho`: the mixing number, ρ ≤ μ, (i.e., the number of parents involved in the procreation of an offspring)
  * `λ`/`lambda`: the number of offspring
  * `selection`: the selection strategy `:plus` or `:comma` (default: `:plus`)
  * `metrics` is a collection of convergence metrics.
