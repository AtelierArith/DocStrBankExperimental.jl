```
get_volatility(
    covar::CovarianceMatrix,
    asset1::Symbol,
    time_period_per_unit::Dates.Period = covar.time_period_per_unit,
)
```

Get the volatility for a stock from a `CovarianceMatrix`.

### Inputs

  * `covar` - A `CovarianceMatrix`
  * `asset1` - A `Symbol` representing an asset.
  * `time_period_per_unit` - The time interval the volatilities will be for.

### Returns

  * A Scalar (the volatility).
