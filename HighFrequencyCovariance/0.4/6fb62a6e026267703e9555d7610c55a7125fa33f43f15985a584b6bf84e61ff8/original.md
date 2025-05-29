```
preaveraged_covariance(
    ts::SortedDataFrame,
    assets::Vector{Symbol} = get_assets(ts);
    regularisation::Union{Missing,Symbol} = :covariance_default,
    drop_assets_if_not_enough_data::Bool = false,
    regularisation_params::Dict = Dict(),
    only_regulise_if_not_PSD::Bool = false,
    theta::Real = 0.15,
    g::NamedTuple = g,
)
```

Estimation of the CovarianceMatrix using preaveraging method.

### Inputs

  * `ts` - The tick data.
  * `assets` - The assets you want to estimate volatilities for.
  * `regularisation` - A symbol representing what regularisation technique should be used. If missing no regularisation is performed.
  * `drop_assets_if_not_enough_data` - If we do not have enough data to estimate for all the input `assets` should we just calculate the correlation/volatilities for those assets we do have?
  * `regularisation_params` - keyword arguments to be consumed in the regularisation algorithm.
  * `only_regulise_if_not_PSD` - Should regularisation only be attempted if the matrix is not psd already.
  * `theta` - A theta value. See paper for details.
  * `g` - A tuple containing a preaveraging method function (with name "f") and a ψ (with name "psi") value.   psi here should be the integral of the function over the interval between zero and one.

### Returns

  * A `CovarianceMatrix`.

### References

Christensen K, Podolskij M, Vetter M (2013). “On covariation estimation for multivariate continuous Itô semimartingales with noise in non-synchronous observation schemes.” Journal of Multivariate Analysis, 120, 59–84. doi:10.1016/j.jmva.2013.05.002.
