```julia
final_time(
    ocp::CTModels.Model{<:CTModels.TimesModel{<:CTModels.AbstractTimeModel, CTModels.FreeTimeModel}},
    variable::Real
) -> Real

```

Get the final time from the model, for a free final time.
