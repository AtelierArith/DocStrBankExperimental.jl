```
GeneticAlgorithm(
    local_search::AbstractAlgorithm
    verbose::Bool = DEFAULT_VERBOSE
    max_iterations::Integer = 200
    max_iterations_without_improvement::Integer = 150
    π_min::Integer = 40
    π_max::Integer = 50
)
```

GeneticAlgorithm represents a clustering algorithm that utilizes a genetic algorithm approach to optimize cluster assignments. It combines evolutionary computation and local search elements to find high-quality clustering solutions.

# Fields

  * `local_search`: the clustering algorithm applied to improve the solution in each meta-heuristics iteration.
  * `verbose`: controls whether the algorithm should display additional information during execution.
  * `max_iterations`: represents the maximum number of iterations the algorithm will perform before stopping.
  * `max_iterations_without_improvement`: represents the maximum number of iterations allowed without improving the best solution.
  * `π_max`: the maximum population size used in the genetic algorithm.
  * `π_min`: the minimum population size used in the genetic algorithm.

# References
