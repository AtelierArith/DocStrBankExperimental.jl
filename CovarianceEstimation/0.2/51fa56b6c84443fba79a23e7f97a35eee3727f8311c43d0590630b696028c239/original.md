```
cov(ans::AnalyticalNonlinearShrinkage, X, [weights]; dims=1, mean=nothing)
```

Nonlinear covariance estimator derived from the sample covariance estimator `S` and its eigenvalue decomposition (which can be given through `decomp`). See Ledoit and Wolf's paper http://www.econ.uzh.ch/static/wp/econwp264.pdf The keyword `mean` can be `nothing` (centering via estimated mean), zero (no centering) or a provided vector. In the first case, a rank-1 modification is applied and therefore the effective sample size is decreased by one (see `analytical_nonlinear_shrinkage`). In the latter two case the mean cannot have been estimated on the data (otherwise the effective sample size will be 1 larger than it should be resulting in numerical instabilities). If you are unsure, use either `nothing` or provide an explicit (non-estimated) vector (possibly a zero vector) and avoid the use of `mean=0`.

  * Time complexity (including formation of `S`)

      * (p<n): O(np^2 + n^2) with moderate constant
      * (p>n): O(p^3) with low constant (dominated by eigendecomposition of S)
