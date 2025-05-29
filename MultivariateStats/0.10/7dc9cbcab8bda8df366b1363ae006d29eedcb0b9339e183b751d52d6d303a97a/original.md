```
fit(PCA, X; ...)
```

Perform PCA over the data given in a matrix `X`. Each column of `X` is an **observation**.

**Keyword arguments**

  * `method`: The choice of methods:

      * `:auto`: use `:cov` when `d < n` or `:svd` otherwise (*default*).
      * `:cov`: based on covariance matrix decomposition.
      * `:svd`: based on SVD of the input data.
  * `maxoutdim`: The output dimension, i.e. dimension of the transformed space (*min(d, nc-1)*)
  * `pratio`: The ratio of variances preserved in the principal subspace (*0.99*)
  * `mean`: The mean vector, which can be either of

      * `0`: the input data has already been centralized
      * `nothing`: this function will compute the mean (*default*)
      * a pre-computed mean vector

**Notes:**

  * The output dimension `p` depends on both `maxoutdim` and `pratio`, as follows. Suppose the first `k` principal components preserve at least `pratio` of the total variance, while the first `k-1` preserves less than `pratio`, then the actual output dimension will be $\min(k, maxoutdim)$.
  * This function calls [`pcacov`](@ref) or [`pcasvd`](@ref) internally, depending on the choice of method.
