```julia
remove_component!(
    _::Type{T<:PowerSystems.Component},
    sys::PowerSystems.System,
    name::AbstractString
)

```

Remove a component from the system by its name.

Throws ArgumentError if the component is not stored.
