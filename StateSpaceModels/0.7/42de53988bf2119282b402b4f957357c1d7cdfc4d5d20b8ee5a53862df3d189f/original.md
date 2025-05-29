```
forecast(model::StateSpaceModel, steps_ahead::Int; kwargs...)
forecast(model::StateSpaceModel, exogenous::Matrix{Fl}; kwargs...) where Fl
```

Forecast the mean and covariance for future observations from a StateSpaceModel.
