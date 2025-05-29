```julia
get_subsystems(
    sys::PowerSystems.System
) -> Base.KeySet{String, Dict{String, Set{Base.UUID}}}

```

Return an iterator of all subsystem names in the system.
