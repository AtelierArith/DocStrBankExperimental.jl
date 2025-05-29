```julia
check_component(
    sys::PowerSystems.System,
    component::PowerSystems.Component
)

```

Check the values of a component.

Throws InvalidValue if any of the component's field values are outside of defined valid range or if the custom validate method for the type fails its check.
