```
robhatreg(X, y)
```

Perform robust regression using the robust hat matrix method.

# Arguments

  * `X::AbstractMatrix`: The design matrix.
  * `y::AbstractVector`: The response vector.

# Returns

  * A dictionary containing the following
  * `betas::AbstractVector`: The estimated coefficients.

# References

Satman, Mehmet Hakan, A robust initial basic subset selection  method for outlier detection algorithms in linear regression, In Press
