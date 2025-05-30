```julia
initial_time(
    ocp::CTModels.Model{<:CTModels.TimesModel{CTModels.FreeTimeModel}},
    variable::AbstractArray{T<:Real, 1}
) -> Any

```

Get the initial time from the model, for a free initial time.
