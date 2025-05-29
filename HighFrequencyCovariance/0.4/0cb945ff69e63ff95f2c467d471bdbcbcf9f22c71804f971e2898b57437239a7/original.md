```
simple_volatility(
   ts::SortedDataFrame,
   assets::Vector{Symbol} = get_assets(ts);
   time_grid::Union{Missing,Dict} = missing,
   fixed_spacing::Union{Missing,Dict,<:Real} = missing,
   use_all_obs::Bool = false,
   rough_guess_number_of_intervals::Integer = 5,
)
```

Calculates volatility with the simple method.

### Inputs

  * `ts` - The tick data.
  * `assets` - The assets you want to estimate volatilities for.
  * `time_grid` - The grid with which to calculate returns. If missing one is generated with a fixed spacing (if that is provided) or a default spacing.
  * `fixed_spacing` - A spacing used to calculate a time grid. Not used if a `time_grid` is input or if `use_all_obs = true`.
  * `use_all_obs` - Use all observations to estimate volatilities. Not used if a `time_grid` is provided.
  * `rough_guess_number_of_intervals` - A rough number of intervals to calculate a default spacing. Not used if a `time_grid` or `fixed_spacing` is provided or if `use_all_obs = true`.

### Returns

  * A `Dict` with an estimated volatility for each asset.
