```
volatility(covar::ForwardCovariance, index::Integer, on::Union{Date,DateTime})
volatility(covar::ForwardCovariance, id::Symbol, on::Union{Date,DateTime})
```

Get the volatility of an `ForwardCovariance` on a date.

### Inputs

  * `covar` - An `ForwardCovariance` that you want the volatility for.
  * `index` - The key of the ito dict that you are interested in
  * `on` The time or instant you want the volatility for.

### Returns

  * A scalar
