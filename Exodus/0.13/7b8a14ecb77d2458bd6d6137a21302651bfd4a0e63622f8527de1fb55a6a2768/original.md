```julia
read_values(
    exo::Exodus.ExodusDatabase,
    t::Type{Exodus.NodalVariable},
    timestep::Integer,
    name::String
) -> Any

```

Wrapper method for nodal variables
