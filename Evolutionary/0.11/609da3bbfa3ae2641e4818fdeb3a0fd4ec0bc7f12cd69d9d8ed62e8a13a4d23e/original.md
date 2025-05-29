Non-dominated Sorting Genetic Algorithm (NSGA-II) for Multi-objective Optimization

The constructor takes following keyword arguments:

  * `populationSize`: The size of the population
  * `crossoverRate`: The fraction of the population at the next generation, that is created by the crossover function
  * `mutationRate`: Probability of chromosome to be mutated
  * `selection`: [Selection](@ref) function (default: `tournament`)
  * `crossover`: [Crossover](@ref) function (default: `SBX`)
  * `mutation`: [Mutation](@ref) function (default: `PLM`)
  * `metrics` is a collection of convergence metrics.
