```
get_partial_information_decomposition(xyz; <keyword arguments>)
```

# Arguments:

  * `xyz`: the 3D frequencies or probabilities.
  * `estimator="maximum_likelihood"`: the entropy estimator.
  * `base=2`: the base of the logarithm, equivalent to the units of information.
  * `probabilities=false`: whether `xyz` is probabilities. If `false`, `xyz` is frequencies.
  * `lambda=nothing`: the shrinkage instensity, only used if `estimator` is `"shrinkage"`.
  * `prior=1`: the Dirichlet prior, only used if `estimator` is `"dirichlet"`.
  * `all_orientations=false`: whether to use each set of values as the target. If `false`, only `values_z` is the target.
  * `include_unique=true`: whether to get the unique information.
  * `include_synergy=true`: whether to get the synergy.
