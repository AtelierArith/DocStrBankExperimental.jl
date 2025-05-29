```
cross_validation(model::StateSpaceModel, steps_ahead::Int, start_idx::Int;
         n_scenarios::Int = 10_000,
         filter::KalmanFilter=default_filter(model),
         optimizer::Optimizer=default_optimizer(model)) where Fl
```

Makes rolling window estimating and forecasting to benchmark the forecasting skill of the model in for different time periods and different lead times. The function returns a struct with the MAE and mean CRPS per lead time. See more on [Cross validation of the forecasts of a model](@ref)

# References

  * DTU course "31761 - Renewables in electricity markets" available on youtube https://www.youtube.com/watch?v=Ffo8XilZAZw&t=556s
