```
latest_value(
    ts::SortedDataFrame,
    at_times::Vector{<:Real};
    assets::Vector{Symbol} = get_assets(ts),
)
```

Get the latest price at a each input time.

### Inputs

  * `ts` - The tick data.
  * `at_times` - The times you want the latest prices for.
  * `assets` - The assets you want latest prices for.

### Returns

  * A `DataFrame`. Rows are for each time specified in at_times. Columns are for each asset.
