Implementation of Koza-type (tree-based) Genetic Programming

The constructor takes following keyword arguments:

  * `populationSize`: The size of the population
  * `terminals`: A dictionary of terminals with their their corresponding dimensionality

      * This dictionary contains (`Terminal`, `Int`) pairs
      * The terminals can be any symbols (variables), constat values, or 0-arity functions.
  * `functions`: A collection of functions with their corresponding arity.

      * This dictionary contains (`Function`, `Int`) pairs
  * `initialization`: A strategy for population initialization (default: `:grow`)

      * Possible values: `:grow` and `:full`
  * `mindepth`: Minimal depth of the expression (default: `0`)
  * `maxdepth`: Maximal depth of the expression (default: `3`)
  * `mutation`: A mutation function (default: [`crosstree`](@ref))
  * `crossover`: A crossover function (default: [`subtree`](@ref))
  * `simplify`: An expression simplification function (default: `:nothing`)
  * `optimizer`: An evolutionary optimizer used for evolving the expressions (default: [`GA`](@ref))

      * Use `mutation` and `crossover` parameters to specify GP-related mutation operation.
      * Use `selection` parameter to specify the offspring selection procedure
