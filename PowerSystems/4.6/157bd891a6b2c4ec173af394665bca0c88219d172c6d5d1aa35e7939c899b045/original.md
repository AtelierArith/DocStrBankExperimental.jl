```julia
convert_component!(
    sys::PowerSystems.System,
    old_load::PowerSystems.PowerLoad,
    new_type::Type{PowerSystems.StandardLoad};
    kwargs...
)

```

Converts a PowerLoad component to a StandardLoad component and replaces the original in the system. Does not set any fields in StandardLoad that lack a PowerLoad equivalent.
