```
cov_to_cor(cov::Array{<:Real, 2})
```

Convert a covariance matrix `cov` to a correlation matrix and a vector of uncertainty values.

Returns a matrix and a vector. Throws a warning when the covariance matrix is not positive definite.

Example:

```julia
cor, unc = cov_to_cor(cov)
```
