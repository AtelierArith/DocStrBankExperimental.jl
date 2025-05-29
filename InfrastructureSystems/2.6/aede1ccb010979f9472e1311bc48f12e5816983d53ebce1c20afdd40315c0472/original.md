```julia
Scenarios(
    name::AbstractString,
    input_data::AbstractDict{Dates.DateTime, <:TimeSeries.TimeArray};
    normalization_factor,
    scaling_factor_multiplier
) -> InfrastructureSystems.Scenarios

```

Construct Scenarios from a Dict of TimeArrays.

# Arguments

  * `name::AbstractString`: user-defined name
  * `input_data::AbstractDict{Dates.DateTime, TimeSeries.TimeArray}`: time series data.
  * `normalization_factor::NormalizationFactor = 1.0`: optional normalization factor to apply to each data entry
  * `scaling_factor_multiplier::Union{Nothing, Function} = nothing`: If the data are scaling factors then this function will be called on the component and applied to the data when [`get_time_series_array`](@ref) is called.
  * `timestamp = :timestamp`: If the values are DataFrames is passed then this must be the column name that contains timestamps.
