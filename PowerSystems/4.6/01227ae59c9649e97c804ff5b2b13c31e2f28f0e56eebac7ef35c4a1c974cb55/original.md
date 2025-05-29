```julia
get_buses(
    sys::PowerSystems.System,
    bus_numbers::Set{Int64}
) -> Vector{PowerSystems.ACBus}

```

Return all buses values with bus_numbers.
