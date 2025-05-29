```
time_between_refreshes(
   ts::SortedDataFrame;
   assets::Vector{Symbol} = get_assets(ts),
)
```

Get a `DataFrame` showing how many time is between each refresh and how many ticks in total.

### Inputs

  * `ts` - Tick data.
  * `assets` - A `Vector` of labels.

### Returns

  * A `DataFrame` summarising the average number of time between ticks for each asset.
