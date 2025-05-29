```
get_draws(covar::ForwardCovariance; uniform_draw::Array{T,1} = rand(length(covar.covariance_labels_))) where T<:Real
```

### Inputs

  * `covar` - An `ForwardCovariance` or `SimpleCovariance` struct that you want to draw from.
  * `uniform_draw`- The draw vector (from the uniform distribution)

### Returns

  * A Dict of draws.
