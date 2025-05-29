```
vegas(f, st, en, kwargs...)
```

VEGAS is a Monte Carlo algorithm for  multidimensional integration based on  adaptive importance sampling. It divides each dimension into bins and adaptively adjusts bin widths so the points sampled from the region where the function has highest magnitude. 

## Arguments:

  * st: Array of starting values in each dimension.

Defaults to zeros(2)

  * end: Array of ending values in each dimension.

Defaults to ones(2)

## Kwargs:

  * nbins: Number of bins in each dimension.

Defaults to 1000. 

  * ncalls: Number of function calls per iteration.

Defaults to 10000.

  * maxiter: Maximum number of iterations.

Defaults to 10.

  * rtol: Relative tolerance required.

Defaults to 1e-4.

  * atol: Absolute tolerance required.

Defaults to 1e-2.

  * debug: Prints `abs(sd/I)` every 100 iterations.

Defaults to false.

  * batch: Whether `f` returns batches of function

evaluations. `f` is assumed to take one argument  `pts`, an `ncalls ×`ndims`matrix. Each row is a unique point and returns an`ncalls` length vector of function evals. This argument defaults to false. 

## Output:

A VEGASResult object with the following fields:

  * Estimate for the integral
  * Standard deviation
  * χ^2 / (numiter - 1): should be less than 1

otherwise integral estimate should not be trusted. 

  * final adapted map

## References:

  * Lepage, G. Peter. "A new algorithm for adaptive

multidimensional integration." Journal of  Computational Physics 27.2 (1978): 192-203.

  * Lepage, G. Peter. "Adaptive multidimensional

integration: VEGAS enhanced." Journal of  Computational Physics 439 (2021): 110386.
