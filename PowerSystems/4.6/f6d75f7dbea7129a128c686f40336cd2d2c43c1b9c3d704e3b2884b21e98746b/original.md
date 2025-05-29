```julia
set_name!(
    component::PowerSystems.Component,
    name::AbstractString
) -> AbstractString

```

Set the name of a component.

Throws an exception if the component is attached to a system.
