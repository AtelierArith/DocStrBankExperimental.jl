```
modelpredict(data::RheoTimeData, model::RheoModelClass; diff_method="BD", kwargs...)
```

Variation of `modelpredict` that takes a `RheoModelClass` and parameter values rather than an already created model. This speeds up the analysis when a large number of different parameter values need to be screened, as only the relevant modulus function is created for the purpose of model prediction.
