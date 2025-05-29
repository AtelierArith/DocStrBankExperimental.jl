```
estimate_volatility(
    ts::SortedDataFrame,
    assets::Vector{Symbol} = get_assets(ts),
    method::Symbol = :two_scales_volatility;
    time_grid::Union{Missing,Dict} = missing,
    fixed_spacing::Union{Missing,Dict,<:Real} = missing,
    use_all_obs::Bool = false,
    rough_guess_number_of_intervals::Integer = 5,
    num_grids::Real = default_num_grids(ts),
)
```

This is a convenience wrapper for the two volatility estimation techniques included in this package.

### General Inputs

  * `ts` - The tick data.
  * `assets` - What assets from ts that you want to estimate the covariance for.
  * `method` - The method can be `:simple_volatility` (for the simple volatility method) or `:two_scales_volatility` (for the two scales volatility method)

#### Inputs only used in `:simple_volatility` method.

  * `time_grid` - The grid with which to calculate returns. If missing one is generated with a fixed spacing (if that is provided) or a default spacing.
  * `fixed_spacing` - A spacing used to calculate a time grid. Not used if a `time_grid` is input or if `use_all_obs = true`.
  * `use_all_obs` - Use all observations to estimate volatilities. Not used if a `time_grid` is provided.
  * `rough_guess_number_of_intervals` - A rough number of intervals to calculate a default spacing. Not used if a `time_grid` or `fixed_spacing` is provided or if `use_all_obs = true`.

#### Inputs only used in `:two_scales_volatility` method.

  * `num_grids` - Number of grids used in order in two scales estimation.

### Returns

  * A `Dict` with estimated volatilities for each asset.
