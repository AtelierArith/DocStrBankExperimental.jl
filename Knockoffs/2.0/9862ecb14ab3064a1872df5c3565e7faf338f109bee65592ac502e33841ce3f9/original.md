```
solve_group_mvr_hybrid(Σ, groups, [outer_iter=100], [inner_pca_iter=1],
    [inner_ccd_iter=1], [tol=0.0001], [ϵ=1e-6], [m=1], [robust=false], [verbose=false])
```

Solves the group-knockoff optimization problem based on MVR objective. Users should call `solve_s_group` instead of this function. 

# Inputs

  * `Σ`: Correlation matrix
  * `groups`: Group membership vector

# Optional inputs

  * `outer_iter`: Maximum number of outer iterations. Each outer iteration will   perform `inner_pca_iter` PCA updates `inner_ccd_iter` full optimization    updates (default = 100).
  * `inner_pca_iter`: Number of full PCA updates before changing to fully   general coordinate descent updates (default = 1)
  * `inner_ccd_iter`: Number of full general coordinate descent updates before changing   to PCA updates (default = 1)
  * `tol`: convergence tolerance. Algorithm converges when    `abs((obj_new-obj_old)/obj_old) < tol` OR when changes in `S` matrix falls    below 1e-4
  * `ϵ`: tolerance added to the lower and upper bound, prevents numerical issues   (default = `1e-6`)
  * `m`: Number of knockoffs per variable (defaults `1`)
  * `robust`: whether to use "robust" Cholesky updates. If `robust=true`, alg will   be ~10x slower, only use this if `robust=false` causes cholesky updates to fail.   (default `false`)
  * `verbose`: Whether to print intermediate results (default `false`)
