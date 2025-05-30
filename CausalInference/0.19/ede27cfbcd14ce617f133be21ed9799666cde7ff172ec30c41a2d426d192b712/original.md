```
exactscorebased(X; method=:gaussian_bic, penalty=0.5, parallel=false, verbose=false)
```

Compute a CPDAG for the given observed data `X` (variables in columns) using the exact algorithm proposed by Silander and Myllymäki (2006) for optimizing the BIC score (or any decomposable score).   The complexity is n*2^n and the algorithm should scale up to ~20-25 variables, afterwards memory becomes a problem.

  * Silander, T., & Myllymäki, P. (2006). A simple approach for finding the globally optimal Bayesian network structure. In Uncertainty in Artificial Intelligence (pp. 445-452).
