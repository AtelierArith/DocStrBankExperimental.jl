```julia
get_time_series_multiple(
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute};
    ...
) -> Union{Tuple{}, Channel{Any}}
get_time_series_multiple(
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    filter_func;
    type,
    name,
    resolution
) -> Union{Tuple{}, Channel{Any}}

```

Returns an iterator of TimeSeriesData instances attached to the component or attribute.

Note that passing a filter function can be much slower than the other filtering parameters because it reads time series data from media.

Call `collect` on the result to get an array.

# Arguments

  * `owner::TimeSeriesOwners`: component or attribute from which to get time_series
  * `filter_func = nothing`: Only return time_series for which this returns true.
  * `type::Union{Nothing, ::Type{<:TimeSeriesData}} = nothing`: Only return time_series with this type.
  * `name::Union{Nothing, AbstractString} = nothing`: Only return time_series matching this value.
  * `resolution::Union{Nothing, Dates.Period} = nothing`: Only return time_series matching this value.

See also: [`get_time_series_multiple` from a `System`](@ref get_time_series_multiple(     data::SystemData,     filter_func = nothing;     type = nothing,     name = nothing, ))
