```
StanProblem(model::BridgeStan.StanModel; nan_on_error::Bool=false)
```

A wrapper for an unconstrained Stan model with data, implementing the [LogDensityProblems](https://www.tamaspapp.eu/LogDensityProblems.jl/) interface.

If `nan_on_error=true`, then any errors from Stan will be suppressed, and `NaN`s will be returned.
