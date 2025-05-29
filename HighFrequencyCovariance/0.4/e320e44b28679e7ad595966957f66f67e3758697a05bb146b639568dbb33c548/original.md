```
two_scales_volatility(vals::Vector, times::Vector, num_grids::Real)
```

Calculates volatility with the two scales method of Zhang, Mykland, Ait-Sahalia 2005. The amount of time for the grid spacing is by default this is a tenth of the total duration by default. If this doesn't make sense for your use of it then choose a spacing at which you expect the effect of microstructure noise will be small.

### Inputs

  * `vals` - The prices at each instant in time.
  * `times` - The times corresponding to each element in `vals`.
  * `num_grids` - Number of grids used in order in two scales estimation.

### Returns

  * A scalar for the estimated volatility of the asset.
  * A scalar for the estimated microstructure noise variance.

    two*scales*volatility(       ts::SortedDataFrame,       assets::Vector{Symbol} = get*assets(ts);       num*grids::Real = default*num*grids(ts),   )

Calculates volatility with the two scales method of Zhang, Mykland, Ait-Sahalia 2005. The amount of time for the grid spacing is by default this is a tenth of the total duration by default. If this doesn't make sense for your use of it then choose a spacing at which you expect the effect of microstructure noise will be small.

### Inputs

  * `ts` - The tick data.
  * `assets` - The assets you want to estimate volatilities for.
  * `num_grids` - Number of grids used in order in two scales estimation.

### Returns

  * A  `Dict` with estimated volatilities for each asset.
  * A  `Dict` with estimated microstructure noise variances for each asset.

### References

Zhang L, Mykland PA, Aït-Sahalia Y (2005). "A Tale of Two Time Scales: Determining Integrated Volatility with Noisy High-Frequency Data." Journal of the American Statistical Association, 100(472), 1394–1411. ISSN 01621459. doi:10.1198/016214505000000169.
