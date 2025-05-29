```
volatility(ito::ItoSet, ito_integral_id::Symbol, on::Union{Date,DateTime})
```

Get volatility of an `ito_integral` on a date.

### Inputs

  * `ito` - An `ItoSet` that you want the volatility for.
  * `ito_integral_id` - The key of the ito dict that you are interested in
  * `on` The time or instant you want the volatility for.

### Returns

  * A scalar
