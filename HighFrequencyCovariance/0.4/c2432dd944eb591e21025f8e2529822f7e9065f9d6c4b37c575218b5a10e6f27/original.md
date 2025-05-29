```
bnhls_covariance(
    ts::SortedDataFrame,
    assets::Vector{Symbol} = get_assets(ts);
    regularisation::Union{Missing,Symbol} = :covariance_default,
    regularisation_params::Dict = Dict(),
    only_regulise_if_not_PSD::Bool = false,
    kernel::HFC_Kernel{<:Real} = parzen,
    H::Real = kernel.c_star * (mean(map(a -> length(ts.groupingrows[a]), assets)))^0.6,
    m::Integer = 2,
)
```

This calculates covariance with the Multivariate realised kernel oof BNHLS(2011).

### Inputs

  * `ts` - The tick data.
  * `assets` - The assets you want to estimate volatilities for.
  * `regularisation` - A symbol representing what regularisation technique should be used. If missing no regularisation is performed.
  * `regularisation_params` - keyword arguments to be consumed in the regularisation algorithm.
  * `only_regulise_if_not_PSD` - Should regularisation only be attempted if the matrix is not psd already.
  * `kernel` - The kernel used. See the paper for details.
  * `H` - The number of lags/leads used in estimation. See the paper for details.
  * `m` - The number of end returns to average.

### Returns

  * A `CovarianceMatrix`.

### References

Barndorff-Nielsen, O., Hansen, P.R., Lunde, A., Shephard, N. 2011. - The whole paper but particularly 2.2, 2.3 here. Kernels are in table 1. choices of H are discussed in section 3.4 of the paper.
