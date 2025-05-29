```
search_cv(estimator, X, y, splits, params; [verbosity = 1])
```

Exhaustive search over the specified sets of parameter values for the `estimator` with features data `X` and label `y`. The iterable `splits` provides vectors of indices for the training dataset. The remaining indices are used to create the validation dataset. Alternatively, search_cv can be called with an input Dataset class

Return an array with a tuple for each set of parameters value, where the first entry is a set of parameter values and the second entry the cross-validation outcome of those values. This outcome is a dictionary with an entry for the validation dataset and, if the parameter `is_provide_training_metric` is set in the `estimator`, an entry for the training dataset. Each entry of the dictionary is another dictionary with an entry for each validation metric in the `estimator`. Each of these entries is an array that holds the validation metric's value for each dataset, at the last valid iteration.

# Arguments

  * `estimator::LGBMEstimator`: the estimator to be fit.
  * `X::Matrix{TX<:Real}`: the features data.
  * `y::Vector{Ty<:Real}`: the labels.
  * `dataset::Dataset`: prepared dataset (either (X, y), or dataset needs to be specified as input)
  * `splits`: the iterable providing arrays of indices for the training dataset.
  * `params`: the iterable providing dictionaries of pairs of parameters (Symbols) and values to   configure the `estimator` with.
  * `verbosity::Integer`: keyword argument that controls LightGBM's verbosity. `< 0` for fatal logs   only, `0` includes warning logs, `1` includes info logs, and `> 1` includes debug logs.
