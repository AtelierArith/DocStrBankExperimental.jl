```julia
initial_time(
    ocp::CTModels.Model{<:CTModels.TimesModel{CTModels.FreeTimeModel}},
    variable::Real
) -> Real

```

Get the initial time from the model, for a free initial time.
