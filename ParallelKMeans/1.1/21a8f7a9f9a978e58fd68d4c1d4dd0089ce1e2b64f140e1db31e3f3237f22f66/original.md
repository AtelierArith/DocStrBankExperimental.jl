```
kmeans([alg::AbstractKMeansAlg,] design_matrix, k; n_threads = nthreads(),
k_init="k-means++", max_iters=300, tol=1e-6, verbose=true, rng = Random.GLOBAL_RNG)
```

This main function employs the K-means algorithm to cluster all examples in the training data (design_matrix) into k groups using either the `k-means++` or random initialisation technique for selecting the initial centroids.

At the end of the number of iterations specified (max_iters), convergence is achieved if difference between the current and last cost objective is less than the tolerance level (tol). An error is thrown if convergence fails.

Arguments:

  * `alg` defines one of the algorithms used to calculate `k-means`. This

argument can be omitted, by default Lloyd algorithm is used.

  * `n_threads` defines number of threads used for calculations, by default it is equal

to the `Threads.nthreads()` which is defined by `JULIA_NUM_THREADS` environmental variable. For small size design matrices it make sense to set this argument to 1 in order to avoid overhead of threads generation.

  * `k_init` is one of the algorithms used for initialization. By default `k-means++` algorithm is used,

alternatively one can use `rand` to choose random points for init.

  * `max_iters` is the maximum number of iterations
  * `tol` defines tolerance for early stopping.
  * `verbose` is verbosity level. Details of operations can be either printed or not by setting verbose accordingly.

A `KmeansResult` structure representing labels, centroids, and sum_squares is returned.
