```julia
final_time(
    ocp::CTModels.Model{<:CTModels.TimesModel{<:CTModels.AbstractTimeModel, CTModels.FixedTimeModel{T<:Real}}}
) -> Real

```

Get the final time from the model, for a fixed final time.
