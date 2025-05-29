```julia
get_subsystem_components(
    sys::PowerSystems.System,
    subsystem_name::AbstractString
) -> Base.Generator{Set{Base.UUID}, InfrastructureSystems.var"#450#451"{InfrastructureSystems.SystemData}}

```

Return a Generator of all components in the subsystem.

Throws ArgumentError if the subsystem name is not stored.
