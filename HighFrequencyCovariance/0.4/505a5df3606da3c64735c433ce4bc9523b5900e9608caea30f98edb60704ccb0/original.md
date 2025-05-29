```
simple_covariance(
    ts::SortedDataFrame,
    assets::Vector{Symbol} = get_assets(ts);
    regularisation::Union{Missing,Symbol} = :covariance_default,
    regularisation_params::Dict = Dict(),
    only_regulise_if_not_PSD::Bool = false,
    time_grid::Union{Missing,Vector} = missing,
    fixed_spacing::Union{Missing,<:Real} = missing,
    refresh_times::Bool = false,
    rough_guess_number_of_intervals::Integer = 5,
)
```

Estimation of the covariance matrix in the standard textbook way.

### Inputs

  * `ts` - The tick data.
  * `assets` - The assets you want to estimate volatilities for.
  * `regularisation` - A symbol representing what regularisation technique should be used. If missing no regularisation is performed.
  * `regularisation_params` - keyword arguments to be consumed in the regularisation algorithm.
  * `only_regulise_if_not_PSD` - Should regularisation only be attempted if the matrix is not psd already.
  * `time_grid` - The grid with which to calculate returns.
  * `fixed_spacing` - A spacing used to calculate a time grid. Not used if `refresh_times=true`.
  * `refresh_times` - Should refresh times be used to estimate covariance.
  * `rough_guess_number_of_intervals` - A rough number of intervals to calculate a default spacing. Not used if a `time_grid` or `fixed_spacing` is provided or if `refresh_times=true`.

### Returns

  * A `CovarianceMatrix`.
