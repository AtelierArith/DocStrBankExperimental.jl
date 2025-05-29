```
bwsj(X; rtol=0.1, leafsize=10, lower=λ*n^(-1/5)*1e-9, upper=λ*n^(-1/5)*1e9)
```

Bandwidth selection for kernel density estimation using Gaussian kernels. Based on the paper Sheather, S. J., & Jones, M. C. (1991). A reliable data‐based bandwidth selection method for kernel density estimation. Journal of the Royal Statistical Society: Series B (Methodological), 53(3), 683-690.

Solves the equation [ R(K) / (nσ⁴ₖS_D(α₂(h))) ]^(1/5) - h = 0 by root finding, bounding the objective such that each iteration can be terminated when the sign of the objective is known.

  * `rtol` - the relative tolerance for the bandwidth.
  * `leafsize` - Below this size, exact computations are used instead of bounds. Does not impact the accuracy of the result, only the execution time.
  * `lower` - Bandwidth lower bound. There is usally no need to change the bounds.
  * `upper` - Bandwidth upper bound.
