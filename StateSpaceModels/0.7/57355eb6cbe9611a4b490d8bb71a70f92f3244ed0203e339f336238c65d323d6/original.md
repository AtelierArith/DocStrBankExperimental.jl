```
simulate_scenarios(
    model::StateSpaceModel, steps_ahead::Int, n_scenarios::Int;
    filter::KalmanFilter=default_filter(model)
) -> Array{<:AbstractFloat, 3}
```

Samples `n_scenarios` future scenarios via Monte Carlo simulation for `steps_ahead` using the desired `filter`.
