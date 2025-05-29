```julia
remove_subsystem!(
    sys::PowerSystems.System,
    subsystem_name::AbstractString
)

```

Remove a subsystem from the system.

Throws ArgumentError if the subsystem name is not stored.
