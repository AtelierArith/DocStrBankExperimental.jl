```
Kmeans(
    metric::SemiMetric = SqEuclidean()
    verbose::Bool = DEFAULT_VERBOSE
    rng::AbstractRNG = Random.GLOBAL_RNG
    tolerance::Real = DEFAULT_TOLERANCE
    max_iterations::Integer = DEFAULT_MAX_ITERATIONS
)
```

The k-means is a clustering algorithm that aims to partition data into clusters by minimizing the distances between data points and their cluster centroids.

# Fields

  * `metric`: defines the distance metric used to compute the distances between data points and cluster centroids.
  * `verbose`: controls whether the algorithm should display additional information during execution.
  * `rng`: represents the random number generator to be used by the algorithm.
  * `tolerance`: represents the convergence criterion for the algorithm. It determines the maximum change allowed in the centroid positions between consecutive iterations.
  * `max_iterations`: represents the maximum number of iterations the algorithm will perform before stopping, even if convergence has not been reached.

# References

  * Hartigan, John A., and Manchek A. Wong. Algorithm AS 136: A k-means clustering algorithm. Journal of the royal statistical society. series c (applied statistics) 28.1 (1979): 100-108.
  * Lloyd, Stuart. Least squares quantization in PCM. IEEE transactions on information theory 28.2 (1982): 129-137.
