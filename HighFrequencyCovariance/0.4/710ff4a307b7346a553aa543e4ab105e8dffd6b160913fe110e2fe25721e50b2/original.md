```
estimate_covariance(
    ts::SortedDataFrame,
    assets::Vector{Symbol} = get_assets(ts),
    method::Symbol = :preaveraged_covariance;
    regularisation::Union{Missing,Symbol} = :default,
    regularisation_params::Dict = Dict(),
    only_regulise_if_not_PSD::Bool = false,
    time_grid::Union{Missing,Vector} = missing,
    fixed_spacing::Union{Missing,<:Real} = missing,
    refresh_times::Bool = false,
    rough_guess_number_of_intervals::Integer = 5, # General Inputs
    kernel::HFC_Kernel{<:Real} = parzen,
    H::Real = kernel.c_star * mean(a -> length(ts.groupingrows[a]), assets)^0.6,
    m::Integer = 2, # BNHLS parameters
    numJ::Integer = 100,
    num_blocks::Integer = 10,
    block_width::Real = (maximum(ts.df[:, ts.time]) - minimum(ts.df[:, ts.time])) /
                        num_blocks,
    microstructure_noise_var::Dict{Symbol,<:Real} = two_scales_volatility(ts, assets)[2], # Spectral Covariance parameters
    drop_assets_if_not_enough_data::Bool = false,
    theta::Real = 0.15,
    g::NamedTuple = g, # Preaveraging
    equalweight::Bool = false,
    num_grids::Real = default_num_grids(ts),
    min_obs_for_estimation::Integer = 10,
    if_dont_have_min_obs::Real = NaN,
)
```

This is a convenience wrapper for the regularisation techniques.

### General Inputs

  * `ts` - The tick data.
  * `assets` - What assets from ts that you want to estimate the covariance for.
  * `method`  - The method you want to use. This can be `:simple_covariance`, `:bnhls_covariance`, `:spectral_covariance`, `:preaveraged_covariance` or `:two_scales_covariance`.
  * `regularisation` - The regularisation method to use. This can be `:identity_regularisation`, `:eigenvalue_clean`, `:nearest_correlation_matrix` or `:nearest_psd_matrix`. You can also choose `:covariance_default` (which is `:nearest_psd_matrix`) or  `:correlation_default` (which is `:nearest_correlation_matrix`). If missing then the default regularisation method for your chosen covariance estimation method will be used.
  * `regularisation_params` - Keyword arguments that will be used by your chosen regularisation method.
  * `only_regulise_if_not_PSD` - Should the resultant matrix only be regularised if it is not psd.

#### Inputs only used in `:simple_covariance` method.

  * `time_grid` - The grid with which to calculate returns (`:simple_covariance` method only).
  * `fixed_spacing` - A spacing used to calculate a time grid. Not used if `refresh_times=true` (`:simple_covariance` method only).
  * `refresh_times` - Should refresh times be used to estimate covariance (`:simple_covariance` method only).
  * `rough_guess_number_of_intervals` - A rough number of intervals to calculate a default spacing. Not used if a `time_grid` or `fixed_spacing` is provided or if `refresh_times=true` (`:simple_covariance` method only).

#### Inputs only used in `:bnhls_covariance` method.

  * `kernel` - The kernel used. See the bnhls paper for details. (`:bnhls_covariance` method only)
  * `H` - The number of lags/leads used in estimation. See the bnhls paper for details. (`:bnhls_covariance` method only)
  * `m` - The number of end returns to average. (`:bnhls_covariance` method only)

#### Inputs only used in `:spectral_covariance` method.

  * `numJ` - The number of J values. See the paper for details (`:spectral_covariance` method only).
  * `num_blocks` - The number of blocks to split the time frame into. See the preaveraging paper for details (`:spectral_covariance` method only).
  * `block_width` - The width of each block to split the time frame into (`:spectral_covariance` method only).
  * `microstructure_noise_var` - Estimates of microstructure noise variance for each asset (`:spectral_covariance` method only).

#### Inputs only used in `:preaveraged_covariance` method.

  * `drop_assets_if_not_enough_data` - If we do not have enough data to estimate for all the input `assets` should we just calculate the correlation/volatilities for those assets we do have?
  * `theta` - A theta value. See paper for details (`:preaveraged_covariance` method only).
  * `g` - A tuple containing a preaveraging method (with name "f") and a ψ value. See paper for details (`:preaveraged_covariance` method only).

#### Inputs only used in `:two_scales_covariance` method.

  * `equalweight` - Should we use equal weight for the two different linear combinations of assets. If false then an optimal weight is calculated (from volatilities) (`:two_scales_covariance` method only).
  * `num_grids` - Number of grids used in order in two scales estimation (`:two_scales_covariance` method only).
  * `min_obs_for_estimation` - How many observations do we need for estimation. If less than this we use below fallback.
  * `if_dont_have_min_obs` - If we do not have sufficient observations to estimate a correlation then what should be used?

### Returns

  * A `CovarianceMatrix`
