```julia
initialize!(
    output::SpeedyWeather.JLD2Output,
    feedback::SpeedyWeather.AbstractFeedback,
    progn::SpeedyWeather.PrognosticVariables,
    diagn::SpeedyWeather.DiagnosticVariables,
    model::SpeedyWeather.AbstractModel
)

```

Initialize JLD2 `output` by creating a JLD2 file.  To be called just before the first timesteps.
