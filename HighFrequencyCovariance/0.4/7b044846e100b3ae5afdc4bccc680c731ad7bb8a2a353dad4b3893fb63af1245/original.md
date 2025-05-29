```
random_value_in_interval(
   ts::SortedDataFrame,
   at_times::Vector{<:Real};
   assets::Vector{Symbol} = get_assets(ts),
   twister_arb_value_in_interval::MersenneTwister = MersenneTwister(2604),
)
```

Get a random value in an interval. So if you input times 1,7,8 then for the second entry it will pick a random update (if any exist) between times 1 and 7.

### Inputs

  * `ts` - The tick data.
  * `at_times` - The times that seperate the intervals of interest.
  * `assets` - The assets of interest.
  * `twister_arb_value_in_interval` - The RNG used in selecting the random interval.

### Returns

  * A `DataFrame` with prices for each asset from random ticks in each interval.
