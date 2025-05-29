```
get_partial_information_decomposition(values_x, values_y, values_z; <keyword arguments>)
```

Estimate the partial information decomposition between three sets of values.

Performance can be improved by setting `all_orientations`, `include_unique` and `include_synergy` according to the use case.

# Arguments:

  * `values_x`: the data values.
  * `values_y`: a second set of data values.
  * `values_z`: a third set of data values.
  * `estimator="maximum_likelihood"`: the entropy estimator.
  * `base=2`: the base of the logarithm, equqivalent to the units of information.
  * `mode="uniform_width"`: the discretization algorithm.
  * `number_of_bins=0`: the number of bins (will be overridden if `mode` is `"bayesian_blocks"`).
  * `get_number_of_bins=get_root_n`: the method for calculating the number of bins (only called if `number_of_bins` is `0`).
  * `lambda=nothing`: the shrinkage instensity, only used if `estimator` is `"shrinkage"`.
  * `prior=1`: the Dirichlet prior, only used if `estimator` is `"dirichlet"`.
  * `all_orientations=false`: whether to use each set of values as the target. If `false`, only `values_z` is the target.
  * `include_unique=true`: whether to get the unique information.
  * `include_synergy=true`: whether to get the synergy.
