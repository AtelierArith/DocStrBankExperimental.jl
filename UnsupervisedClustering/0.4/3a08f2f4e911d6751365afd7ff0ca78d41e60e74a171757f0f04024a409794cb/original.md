```
Kmedoids(
    verbose::Bool = DEFAULT_VERBOSE
    rng::AbstractRNG = Random.GLOBAL_RNG
    tolerance::Real = DEFAULT_TOLERANCE
    max_iterations::Integer = DEFAULT_MAX_ITERATIONS
)
```

The k-medoids is a variation of k-means clustering algorithm that uses actual data points (medoids) as representatives of each cluster instead of the mean.

# Fields

  * `verbose`: controls whether the algorithm should display additional information during execution.
  * `rng`: represents the random number generator to be used by the algorithm.
  * `tolerance`: represents the convergence criterion for the algorithm. It determines the maximum change allowed in the centroid positions between consecutive iterations.
  * `max_iterations`: represents the maximum number of iterations the algorithm will perform before stopping, even if convergence has not been reached.

# References
