```
covariance(ito1::ItoIntegral,ito2::ItoIntegral, from::Real, to::Real, gaussian_correlation::Real)
covariance(ito1::ItoIntegral,ito2::ItoIntegral, base::Union{Date,DateTime}, from::Union{Date,DateTime}, to::Union{Date,DateTime}, gaussian_correlation::Real)
```

Get the covariance of two `ItoIntegral`s over a certain period given the underlying Brownian processes have a correlation of `gaussian_correlation`.

### Inputs

  * `ito1` - The first `ItoIntegral`
  * `ito2` - The second `ItoIntegral`
  * `from` - The start of the period
  * `to` - The end of the period
  * `gaussian_correlation` - The correlation between the brownians for each of the two itos. This should be in the range [-1,1].
  * `on` - What instant do you want the volatility for.

### Outputs

  * A scalar
