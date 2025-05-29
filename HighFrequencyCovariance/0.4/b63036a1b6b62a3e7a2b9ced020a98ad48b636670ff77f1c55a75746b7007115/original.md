```
ticks_per_asset(ts::SortedDataFrame, assets::Vector{Symbol} = get_assets(ts))
```

Count the number of observations for each asset.

### Inputs

  * `ts` - The tick data
  * `assets` - A vector with asset `Symbol`s.

### Returns

  * A `Dict` with the number of observations for each input asset.
