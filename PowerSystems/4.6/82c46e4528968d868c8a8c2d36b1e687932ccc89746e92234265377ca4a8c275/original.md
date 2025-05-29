```julia
get_supplemental_attributes(
    filter_func::Function,
    _::Type{T<:InfrastructureSystems.SupplementalAttribute},
    sys::PowerSystems.System
) -> InfrastructureSystems.FlattenIteratorWrapper{T, I} where {T<:InfrastructureSystems.SupplementalAttribute, I<:(Vector)}

```

Returns an iterator of supplemental attributes. T can be concrete or abstract. Call collect on the result if an array is desired.

# Examples

```julia
iter = get_supplemental_attributes(GeometricDistributionForcedOutage, sys)
iter = get_supplemental_attributes(Outage, sys)
iter = get_supplemental_attributes(x -> get_mean_time_to_recovery(x) ==  >= 0.5, GeometricDistributionForcedOutage, sys)
outages = get_supplemental_attributes(GeometricDistributionForcedOutage, sys) do outage
    get_mean_time_to_recovery(x) ==  >= 0.5
end
outages = collect(get_supplemental_attributes(GeometricDistributionForcedOutage, sys))
```

See also: [`iterate_supplemental_attributes`](@ref)
