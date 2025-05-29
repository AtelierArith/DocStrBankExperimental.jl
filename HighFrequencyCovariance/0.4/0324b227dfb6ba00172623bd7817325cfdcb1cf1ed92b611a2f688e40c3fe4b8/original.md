```
two_scales_covariance(
    ts::SortedDataFrame,
    assets::Vector{Symbol} = get_assets(ts);
    regularisation::Union{Missing,Symbol} = :correlation_default,
    regularisation_params::Dict = Dict(),
    only_regulise_if_not_PSD::Bool = false,
    equalweight::Bool = false,
    num_grids::Real = default_num_grids(ts),
    min_obs_for_estimation::Integer = 10,
    if_dont_have_min_obs::Real = NaN,
)
```

Estimation of a CovarianceMatrix using the two scale covariance method.

### Inputs

  * `ts` - The tick data.
  * `assets` - The assets you want to estimate volatilities for.
  * `regularisation` - A symbol representing what regularisation technique should be used. If missing no regularisation is performed.
  * `regularisation_params` - keyword arguments to be consumed in the regularisation algorithm.
  * `only_regulise_if_not_PSD` - Should regularisation only be attempted if the matrix is not psd already.
  * `equalweight` - Should we use equal weight for the two different linear combinations of assets. If false then an optimal weight is calculated (from volatilities).
  * `num_grids` - Number of grids used in order in two scales estimation.
  * `min_obs_for_estimation` - How many observations do we need for estimation. If less than this we use below fallback.
  * `if_dont_have_min_obs` - If we do not have sufficient observations to estimate a correlation then what should be used?

### Returns

  * A `CovarianceMatrix`.
