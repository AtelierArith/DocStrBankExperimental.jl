```
correlation(covar::ForwardCovariance, index_1::Integer, index_2::Integer)
correlation(covar::ForwardCovariance, id1::Symbol, id2::Symbol)
```

Get the correlation of two `ItoIntegral`s over a period.

### Inputs

  * `covar` - An `ForwardCovariance` that you want the correlation for.
  * `index_1` or `id1` - The key/index of the first ito that you are interested in
  * `index_2` or `id2` - The key/index of the second ito that you are interested in

### Returns

  * A scalar
