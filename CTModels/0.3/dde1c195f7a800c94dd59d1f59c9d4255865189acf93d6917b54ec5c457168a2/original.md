```julia
initial_time(
    ocp::CTModels.Model{<:CTModels.TimesModel{CTModels.FixedTimeModel{T<:Real}}}
) -> Real

```

Get the initial time from the model, for a fixed initial time.
