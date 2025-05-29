```
MultiStart(
    local_search::AbstractAlgorithm
    verbose::Bool = DEFAULT_VERBOSE
    max_iterations::Integer = 200
)
```

The MultiStart approach repeatedly applies a clustering algorithm to generate multiple solutions with different initial points and selects the best solution.

# Fields

  * `local_search`: the clustering algorithm applied to improve the solution in each meta-heuristics iteration.
  * `verbose`: controls whether the algorithm should display additional information during execution.
  * `max_iterations`: represents the maximum number of iterations the algorithm will perform before stopping.
