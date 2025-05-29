```
get_probabilities(estimator, frequencies; <keyword arguments>)
```

Estimate probabilities from a set of discrete values.

# Arguments:

  * `estimator`: the entropy estimator.
  * `frequencies`: the bin frequencies for the discretized data values.
  * `lambda=nothing`: the shrinkage instensity, only used if `estimator` is `"shrinkage"`.
  * `prior=1`: the Dirichlet prior, only used if `estimator` is `"dirichlet"`.
