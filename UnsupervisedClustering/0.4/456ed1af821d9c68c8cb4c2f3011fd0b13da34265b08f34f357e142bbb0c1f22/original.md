```
GMM(
    estimator::CovarianceMatrixEstimator
    verbose::Bool = DEFAULT_VERBOSE
    rng::AbstractRNG = Random.GLOBAL_RNG
    tolerance::Real = DEFAULT_TOLERANCE
    max_iterations::Integer = DEFAULT_MAX_ITERATIONS
    decompose_if_fails::Bool = true
)
```

The GMM is a clustering algorithm that models the underlying data distribution as a mixture of Gaussian distributions.

# Fields

  * `estimator`: represents the method or algorithm used to estimate the covariance matrices in the GMM.
  * `verbose`: controls whether the algorithm should display additional information during execution.
  * `rng`: represents the random number generator to be used by the algorithm.
  * `tolerance`: represents the convergence criterion for the algorithm. It determines the maximum change allowed in the model's log-likelihood between consecutive iterations before considering convergence.
  * `max_iterations`: represents the maximum number of iterations the algorithm will perform before stopping, even if convergence has not been reached.
  * `decompose_if_fails`: determines whether the algorithm should attempt to decompose the covariance matrix of a component and fix its eigenvalues if the decomposition fails due to numerical issues.

# References

  * Dempster, Arthur P., Nan M. Laird, and Donald B. Rubin. Maximum likelihood from incomplete data via the EM algorithm. Journal of the royal statistical society: series B (methodological) 39.1 (1977): 1-22.
