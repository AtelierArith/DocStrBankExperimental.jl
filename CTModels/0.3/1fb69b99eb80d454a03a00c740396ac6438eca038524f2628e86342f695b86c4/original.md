```julia
final_time(
    model::CTModels.TimesModel{<:CTModels.AbstractTimeModel, CTModels.FreeTimeModel},
    variable::AbstractArray{T<:Real, 1}
) -> Any

```

Get the final time from the times model, from a free final time model.
