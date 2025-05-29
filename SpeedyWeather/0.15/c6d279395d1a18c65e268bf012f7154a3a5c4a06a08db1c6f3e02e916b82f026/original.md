```julia
initialize!(
    model::SpeedyWeather.PrimitiveWet;
    time
) -> SpeedyWeather.Simulation{Model} where Model<:SpeedyWeather.PrimitiveWet

```

Calls all `initialize!` functions for components of `model`, except for `model.output` and `model.feedback` which are always called at in `time_stepping!` and `model.implicit` which is done in `first_timesteps!`.
