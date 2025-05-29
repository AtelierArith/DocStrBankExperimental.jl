```julia
Deterministic(
    name::AbstractString,
    filename::AbstractString,
    component::InfrastructureSystems.InfrastructureSystemsComponent,
    resolution::Dates.Period;
    normalization_factor,
    scaling_factor_multiplier
) -> InfrastructureSystems.Deterministic

```

Construct Deterministic from a CSV file. The first column must be a timestamp in DateTime format and the columns the values in the forecast window.

# Arguments

  * `name::AbstractString`: user-defined name
  * `filename::AbstractString`: name of CSV file containing data
  * `component::InfrastructureSystemsComponent`: component associated with the data
  * `normalization_factor::NormalizationFactor = 1.0`: optional normalization factor to apply to each data entry
  * `scaling_factor_multiplier::Union{Nothing, Function} = nothing`: If the data are scaling factors then this function will be called on the component and applied to the data when [`get_time_series_array`](@ref) is called.
