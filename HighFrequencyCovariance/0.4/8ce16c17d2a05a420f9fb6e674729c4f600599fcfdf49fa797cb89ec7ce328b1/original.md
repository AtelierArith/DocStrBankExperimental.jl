```
get_assets(ts::SortedDataFrame, obs_to_include::Integer = 10)
```

This returns a vector of all of the assets in the `SortedDataFrame` with at least some number of observations (10 by default).

### Inputs

  * `ts` - The tick data.
  * `obs_to_include` - An integer for the minimum number of ticks in `ts` needed for the function to include that asset.

### Returns

  * A `Vector{Symbol}` with each asset.
