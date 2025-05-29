```julia
initialize!(
    model::SpeedyWeather.Barotropic;
    time
) -> SpeedyWeather.Simulation{Model} where Model<:SpeedyWeather.Barotropic

```

Calls all `initialize!` functions for most fields, representing components, of `model`, except for `model.output` and `model.feedback` which are always called at in `time_stepping!`.
