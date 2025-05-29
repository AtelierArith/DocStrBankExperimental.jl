```
log_likelihood(covar::ForwardCovariance, coordinates::Dict{Symbol,Real})
```

get the log likelihood at some coordinates. Note that it is assumed that the mean of the multivariate gaussian is the zero vector.

### Inputs

  * `covar` - the `ForwardCovariance` struct that you want to evaluate the log likelihood.
  * `coordinates` - The coordinates you want to examine.

### Outputs

  * A scalar
