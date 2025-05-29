```julia
has_component(
    sys::PowerSystems.System,
    T::Type{<:PowerSystems.Component},
    name::AbstractString
) -> Bool

```

Check to see if the component of type T with name exists.
