```
fit_marginal(y, X, method=:maxent, ...)
fit_marginal(y, X, μ, Σ, method=:maxent, ...)
```

Generates model-X knockoffs with `method` and computes feature importance statistics based on squared marginal Z score: abs2(x[:, i]^t*y) / n. If `μ` and `Σ` are not provided, they will be estimated from data. 

# Inputs

  * `y`: A `n × 1` response vector
  * `X`: A `n × p` numeric matrix, each row is a sample, and each column is covariate.
  * `method`: Method for knockoff generation (defaults to `:maxent`)
  * `μ`: A `p × 1` vector of column mean of `X`. If not provided, defaults to column mean.
  * `Σ`: A `p × p` covariance matrix of `X`. If not provided, it will be estimated    based on a shrinked empirical covariance matrix, see [`modelX_gaussian_knockoffs`](@ref)
  * `d`: Distribution of response. Defaults `Normal()`, for binary response   (logistic regression) use `Binomial()`.
  * `m`: Number of simultaneous knockoffs to generate, defaults to `m=1`
  * `fdrs`: Target FDRs, defaults to `[0.01, 0.05, 0.1, 0.25, 0.5]`
  * `groups`: Vector of group membership. If not supplied, we generate regular knockoffs.   If supplied, we run group knockoffs.
  * `filter_method`: Choices are `:knockoff` or `:knockoff_plus` (default)
  * `debias`: Defines how the selected coefficients are debiased. Specify `:ls`    for least squares or `:lasso` for Lasso (only running on the    support). To not debias, specify `debias=nothing` (default).
  * `kwargs`: Additional arguments to input into `glmnetcv` and `glmnet`
