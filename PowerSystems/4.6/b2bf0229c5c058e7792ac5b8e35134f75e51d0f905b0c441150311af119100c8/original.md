```julia
get_supplemental_attribute(
    sys::PowerSystems.System,
    uuid::Base.UUID
) -> InfrastructureSystems.SupplementalAttribute

```

Return the supplemental attribute with the given uuid.

Throws ArgumentError if the attribute is not stored.
