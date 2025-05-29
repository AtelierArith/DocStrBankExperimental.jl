```julia
remove_supplemental_attribute!(
    sys::PowerSystems.System,
    component::PowerSystems.Component,
    attribute::InfrastructureSystems.SupplementalAttribute
)

```

Remove the supplemental attribute from the component. The attribute will be removed from the system if it is not attached to any other component.
