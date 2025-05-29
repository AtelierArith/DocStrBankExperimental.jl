```
get_timegrid(
    ts::SortedDataFrame,
    assets::Vector{Symbol},
    time_grid::Missing,
    fixed_spacing::Union{Missing,<:Real},
    refresh_times::Bool,
    rough_guess_number_of_intervals::Integer,
)

get_timegrid(
    ts::SortedDataFrame,
    assets::Vector{Symbol},
    time_grid::Vector,
    fixed_spacing::Union{Missing,<:Real},
    refresh_times::Bool,
    rough_guess_number_of_intervals::Integer,
)
```

This returns a sequence of times at which the SortedDataFrame can be queried for prices. This is used in the simple_covariance method.

### Inputs

  * `ts` - The tick data.
  * `time_grid` - The grid with which to calculate returns.
  * `fixed_spacing` - A spacing used to calculate a time grid. Not used if `refresh_times=true`.
  * `refresh_times` - Should refresh times be used to estimate covariance.
  * `rough_guess_number_of_intervals` - A rough number of intervals to calculate a default spacing. Not used if a `time_grid` or `fixed_spacing` is provided or if `refresh_times=true`.

### Returns

  * A `Vector{<:Real}`.
