```julia
initial_time(
    model::CTModels.TimesModel{CTModels.FreeTimeModel},
    variable::AbstractArray{T<:Real, 1}
) -> Any

```

Get the initial time from the times model, from a free initial time model.
