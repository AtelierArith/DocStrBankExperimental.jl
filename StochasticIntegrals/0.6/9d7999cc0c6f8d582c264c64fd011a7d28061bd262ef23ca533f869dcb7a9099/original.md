```
get_zero_draws(covar::ForwardCovariance)
```

get a draw of zero for all `ItoIntegral`s. This may be handy for bug hunting.

### Inputs

  * covar - the `ForwardCovariance` struct that you want zero draws from

### Outputs

  * A `Dict` of zero draws
