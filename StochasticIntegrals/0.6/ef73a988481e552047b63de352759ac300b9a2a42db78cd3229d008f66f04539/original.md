```
variance(covar::ForwardCovariance, id::Symbol)
variance(covar::ForwardCovariance, index::Integer)
```

Get the variance of an `ForwardCovariance` over a period.

### Inputs

  * `covar` - An `ForwardCovariance` that you want the variance for.
  * `id` or `index` - The key/index of the ito dict that you are interested in

### Returns

  * A scalar
