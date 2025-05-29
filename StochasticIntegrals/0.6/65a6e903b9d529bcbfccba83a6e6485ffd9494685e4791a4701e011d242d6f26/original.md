```
variance(ito::ItoIntegral, from::Real, to::Real)
variance(ito::ItoIntegral, base::Union{Date,DateTime}, from::Union{Date,DateTime}, to::Union{Date,DateTime})
```

Get the variance of an `ItoIntegral` from one point of time to another.

### Inputs

  * `ito` - The `ItoIntegral` you want the variance for.
  * `from` - The time at which the integration starts.
  * `to` - The time at which the integration ends.

### Outputs

  * A scalar
