```julia
remove_component!(
    sys::PowerSystems.System,
    component::PowerSystems.Component
)

```

Remove a component from the system by its value.

Throws ArgumentError if the component is not stored.
