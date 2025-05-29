```
AutoRegressionEmission <: EmissionModel
```

A mutable struct representing an autoregressive emission model, which wraps around an `AutoRegression` model.

# Fields

  * `inner_model::AutoRegression`: The underlying autoregressive model used for the emissions.
