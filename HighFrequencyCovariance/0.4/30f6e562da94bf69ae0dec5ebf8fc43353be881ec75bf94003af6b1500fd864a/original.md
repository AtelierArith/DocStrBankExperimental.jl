```
estimate_microstructure_noise(
    ts::SortedDataFrame,
    assets::Vector{Symbol} = get_assets(ts);
    num_grids::Real = default_num_grids(ts),
)
```

This estimates microstructure noise with the two*scales*volatility method.

### Inputs

  * `ts` - The tick data.
  * `assets` - What assets from ts that you want to estimate the covariance for.
  * `num_grids` - Number of grids used in order in two scales estimation.

### Returns

  * A `Dict` with estimated microstructure noise variances for each asset.
