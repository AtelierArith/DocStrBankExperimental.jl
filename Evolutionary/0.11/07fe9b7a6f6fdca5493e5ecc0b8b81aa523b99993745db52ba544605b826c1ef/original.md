Implementation of Genetic Algorithm

The constructor takes following keyword arguments:

  * `populationSize`: The size of the population
  * `crossoverRate`: The fraction of the population at the next generation, not including elite children, that is created by the crossover function.
  * `mutationRate`: Probability of chromosome to be mutated
  * `ɛ`/`epsilon`: Positive integer specifies how many individuals in the current generation are guaranteed to survive to the next generation. Floating number specifies fraction of population.
  * `selection`: [Selection](@ref) function (default: [`tournament`](@ref))
  * `crossover`: [Crossover](@ref) function (default: [`genop`](@ref))
  * `mutation`: [Mutation](@ref) function (default: [`genop`](@ref))
  * `metrics` is a collection of convergence metrics.
