```
spectral_covariance(
    ts::SortedDataFrame,
    assets::Vector{Symbol} = get_assets(ts);
    regularisation::Union{Missing,Symbol} = :covariance_default,
    regularisation_params::Dict = Dict(),
    only_regulise_if_not_PSD::Bool = false,
    numJ::Integer = 100,
    num_blocks::Integer = 10,
    block_width::Real = (maximum(ts.df[:, ts.time]) - minimum(ts.df[:, ts.time])) /
                        num_blocks,
    microstructure_noise_var::Dict{Symbol,<:Real} = two_scales_volatility(ts, assets)[2],
)
```

Estimation of a CovarianceMatrix using the spectral covariance method.

### Inputs

  * `ts` - The tick data.
  * `assets` - The assets you want to estimate volatilities for.
  * `regularisation` - A symbol representing what regularisation technique should be used. If missing no regularisation is performed.
  * `regularisation_params` - keyword arguments to be consumed in the regularisation algorithm.
  * `only_regulise_if_not_PSD` - Should regularisation only be attempted if the matrix is not psd already.
  * `numJ` - The number of J values. See the paper for details.
  * `num_blocks` - The number of blocks to split the time frame into. See the paper for details.
  * `block_width` - The width of each block to split the time frame into.
  * `microstructure_noise_var` - Estimates of microstructure noise variance for each asset.

### Returns

  * A `CovarianceMatrix`.

### References

Bibinger M, Hautsch N, Malec P, Reiss M (2014). “Estimating the quadratic covariation matrix from noisy observations: Local method of moments and efficiency.” The Annals of Statistics, 42(4), 1312–1346. doi:10.1214/14-AOS1224.
