```
UniqueElements()
```

An [`OutcomeSpace`](@ref) based on straight-forward counting of distinct elements in a univariate time series or multivariate dataset. This is the same as giving no estimator to [`probabilities`](@ref).

## Outcome space

The outcome space is the unique sorted values of the input. Hence, input `x` is needed for a well-defined [`outcome_space`](@ref).

## Implements

  * [`codify`](@ref). Used for encoding inputs where ordering matters (e.g. time series).
