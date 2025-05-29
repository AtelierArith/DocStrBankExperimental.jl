```
get_mutual_information(xy; <keyword arguments>)
```

# Arguments:

  * `xy`: the 2D frequencies or probabilities.
  * `estimator="maximum_likelihood"`: the entropy estimator.
  * `base=2`: the base of the logarithm, equivalent to the units of information.
  * `probabilities=false`: whether `xy` is probabilities. If `false`, `xy` is frequencies.
  * `lambda=nothing`: the shrinkage instensity, only used if `estimator` is `"shrinkage"`.
  * `prior=1`: the Dirichlet prior, only used if `estimator` is `"dirichlet"`.
