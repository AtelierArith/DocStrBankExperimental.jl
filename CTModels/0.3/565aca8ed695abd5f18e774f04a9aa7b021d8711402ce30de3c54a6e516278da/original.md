```julia
final_time(
    ocp::CTModels.Model{<:CTModels.TimesModel{<:CTModels.AbstractTimeModel, CTModels.FreeTimeModel}},
    variable::AbstractArray{T<:Real, 1}
) -> Any

```

Get the final time from the model, for a free final time.
