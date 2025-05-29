```
BasicIndividual(x, t, y, callback; id, initial)
```

# Arguments

  * `x`: Subject specific covariates. If Matrix is passed, predictions can change over time.
  * `t`: Time points of observations. If the subject has time-variable covariates, a NamedTuple (x = [...], y = [...]) should be passed.
  * `y::AbstractVector`: Observations. Must be a vector. Currently only supports a single DV.
  * `callback`: Differential equation callback containing treatment interventions.
  * `id`: Patient id to store in the Individual instance.
  * `initial`: Initial value of the dependent value at t = 0. Default = [].
