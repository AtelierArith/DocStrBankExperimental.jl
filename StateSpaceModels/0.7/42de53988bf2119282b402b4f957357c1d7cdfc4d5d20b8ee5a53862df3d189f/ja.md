```
forecast(model::StateSpaceModel, steps_ahead::Int; kwargs...)
forecast(model::StateSpaceModel, exogenous::Matrix{Fl}; kwargs...) where Fl
```

StateSpaceModelからの将来の観測値の平均と共分散を予測します。
