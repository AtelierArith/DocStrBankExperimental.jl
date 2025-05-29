```
RandomSwap(
    local_search::AbstractAlgorithm
    verbose::Bool = DEFAULT_VERBOSE
    max_iterations::Integer = 200
    max_iterations_without_improvement::Integer = 150
)
```

RandomSwap is a meta-heuristic approach used for clustering problems. It follows an iterative process that combines local optimization with perturbation to explore the search space effectively. A local optimization algorithm is applied at each iteration to converge toward a local optimum. Then, a perturbation operator generates a new starting point and continues the search.

# Fields

  * `local_search`: the clustering algorithm applied to improve the solution in each meta-heuristics iteration.
  * `verbose`: controls whether the algorithm should display additional information during execution.
  * `max_iterations`: represents the maximum number of iterations the algorithm will perform before stopping.
  * `max_iterations_without_improvement`: represents the maximum number of iterations allowed without improving the best solution.

# References

  * Fränti, Pasi. Efficiency of random swap clustering. Journal of big data 5.1 (2018): 1-29.
