```julia
Probabilistic(
    name::AbstractString,
    input_data::AbstractDict,
    percentiles::Vector,
    resolution::Dates.Period;
    normalization_factor,
    scaling_factor_multiplier
) -> InfrastructureSystems.Probabilistic

```

Construct Probabilistic from a SortedDict of Arrays.

# Arguments

  * `name::AbstractString`: user-defined name
  * `input_data::AbstractDict{Dates.DateTime, Matrix{Float64}}`: time series data.
  * `percentiles`: Percentiles represented in the probabilistic forecast
  * `resolution::Dates.Period`: The resolution of the forecast in Dates.Period`
  * `normalization_factor::NormalizationFactor = 1.0`: optional normalization factor to apply to each data entry
  * `scaling_factor_multiplier::Union{Nothing, Function} = nothing`: If the data are scaling factors then this function will be called on the component and applied to the data when [`get_time_series_array`](@ref) is called.
