Implementation of Differential Evolution: DE/**selection**/n/**recombination**

The constructor takes following keyword arguments:

  * `populationSize`: The size of the population
  * `F`: the differentiation (mutation) scale factor (default: 0.9). It's usually defined in range $F \in (0, 1+]$
  * `n`: the number of differences used in the perturbation (default: 1)
  * `selection`: the selection strategy function (default: [`random`](@ref))
  * `recombination`: the recombination functions (default: [`BINX(0.5)`](@ref))
  * `K`: the recombination scale factor (default: 0.5*(F+1))
  * `metrics` is a collection of convergence metrics.
