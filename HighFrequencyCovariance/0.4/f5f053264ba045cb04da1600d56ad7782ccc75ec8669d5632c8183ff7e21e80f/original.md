```
get_all_refresh_times(
    ts::SortedDataFrame,
    assets::Vector{Symbol} = get_assets(ts);
    start_time::R = minimum(ts.df[:, ts.time]),
) where R<:Real
```

Get a vector of all refresh times when all assets have an updated price. So if there are assets A and B that trade at times (1,5,6,7,10) and (2,5,7,9) then the refresh times are (2,5,7,10) as at these four times there are updated prices for all assets that have happened since the previous refresh time.

### Inputs

  * `ts` - The tick data.
  * `assets` - The assets of interest.
  * `start_time` - From what time should we start looking for updated prices.

### Returns

  * A `Vector` of refresh times.
