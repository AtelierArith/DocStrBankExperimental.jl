```julia
final_time(
    model::CTModels.TimesModel{<:CTModels.AbstractTimeModel, <:CTModels.FixedTimeModel{T<:Real}}
) -> Real

```

Get the final time from the times model, from a fixed final time model.
