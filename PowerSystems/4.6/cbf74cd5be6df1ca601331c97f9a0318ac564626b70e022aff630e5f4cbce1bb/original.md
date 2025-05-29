```julia
validate_component_with_system(
    component::PowerSystems.Component,
    sys::PowerSystems.System
) -> Bool

```

Validate a component against System data. Return true if the instance is valid.

Refer to [`validate_component`](@ref) if the validation logic only requires data contained within the instance.
