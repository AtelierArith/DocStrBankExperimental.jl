```julia
remove_component_from_subsystem!(
    sys::PowerSystems.System,
    subsystem_name::AbstractString,
    component::PowerSystems.Component
)

```

Remove a component from a subsystem.

Throws ArgumentError if the subsystem name or component is not stored.
