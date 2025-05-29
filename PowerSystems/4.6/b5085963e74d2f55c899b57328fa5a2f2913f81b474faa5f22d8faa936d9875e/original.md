```julia
remove_supplemental_attributes!(
    _::Type{T<:InfrastructureSystems.SupplementalAttribute},
    sys::PowerSystems.System
)

```

Remove all supplemental attributes with the given type from the system.
