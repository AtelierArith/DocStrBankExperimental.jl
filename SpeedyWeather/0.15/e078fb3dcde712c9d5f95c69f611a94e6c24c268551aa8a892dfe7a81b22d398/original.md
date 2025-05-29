```julia
initialize!(
    model::SpeedyWeather.ShallowWater;
    time
) -> SpeedyWeather.Simulation{Model} where Model<:SpeedyWeather.ShallowWater

```

Calls all `initialize!` functions for most components (=fields) of `model`, except for `model.output` and `model.feedback` which are always initialized in `time_stepping!` and `model.implicit` which is done in `first_timesteps!`.
