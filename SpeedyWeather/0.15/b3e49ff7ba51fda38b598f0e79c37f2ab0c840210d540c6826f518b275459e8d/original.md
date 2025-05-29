```julia
initialize!(
    feedback::SpeedyWeather.Feedback,
    clock::SpeedyWeather.Clock,
    model::SpeedyWeather.AbstractModel
) -> ProgressMeter.Progress

```

Initializes the a `Feedback` struct.
