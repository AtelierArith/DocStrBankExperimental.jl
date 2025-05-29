```julia
SingleTimeSeries(
    name::AbstractString,
    data::Union{DataFrames.DataFrame, TimeSeries.TimeArray};
    normalization_factor,
    scaling_factor_multiplier,
    timestamp
) -> InfrastructureSystems.SingleTimeSeries

```

Construct SingleTimeSeries from a TimeArray or DataFrame.

# Arguments

  * `name::AbstractString`: user-defined name
  * `data::Union{TimeSeries.TimeArray, DataFrames.DataFrame}`: time series data
  * `normalization_factor::NormalizationFactor = 1.0`: optional normalization factor to apply to each data entry
  * `scaling_factor_multiplier::Union{Nothing, Function} = nothing`: If the data are scaling factors then this function will be called on the component and applied to the data when [`get_time_series_array`](@ref) is called.
  * `timestamp = :timestamp`: If a DataFrame is passed then this must be the column name that contains timestamps.
