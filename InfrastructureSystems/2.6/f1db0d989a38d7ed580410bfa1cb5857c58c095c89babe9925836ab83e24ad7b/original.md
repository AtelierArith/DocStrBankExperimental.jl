```julia
SingleTimeSeries(
    name::AbstractString,
    filename::AbstractString,
    component::InfrastructureSystems.InfrastructureSystemsComponent,
    resolution::Dates.Period;
    normalization_factor,
    scaling_factor_multiplier
) -> InfrastructureSystems.SingleTimeSeries

```

Construct SingleTimeSeries from a CSV file. The file must have a column that is the name of the component.

# Arguments

  * `name::AbstractString`: user-defined name
  * `filename::AbstractString`: name of CSV file containing data
  * `component::InfrastructureSystemsComponent`: component associated with the data
  * `resolution::Dates.Period`: resolution of the time series
  * `normalization_factor::NormalizationFactor = 1.0`: optional normalization factor to apply to each data entry
  * `scaling_factor_multiplier::Union{Nothing, Function} = nothing`: If the data are scaling factors then this function will be called on the component and applied to the data when [`get_time_series_array`](@ref) is called.
