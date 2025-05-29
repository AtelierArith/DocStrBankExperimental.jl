```
fit(::Type{M}, X, y; kwarg...) where {M<:RobustLinearModel}
```

Fit a robust model using the `L2Estimator`. It should give the same results as `GLM.lm`.

# Arguments

  * `X`: the model matrix (it can be dense or sparse) or a formula
  * `y`: the response vector or a table (dataframe, namedtuple, ...).
