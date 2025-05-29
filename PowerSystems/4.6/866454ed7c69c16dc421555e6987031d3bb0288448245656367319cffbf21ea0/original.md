```julia
validate_component(
    component::PowerSystems.Component
) -> Bool

```

Validate the component fields using only those fields. Refer to [`validate_component_with_system`](@ref) to use other System data for the validation.

Return true if the instance is valid.
