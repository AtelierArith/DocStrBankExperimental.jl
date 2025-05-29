```julia
read_values(
    exo::Exodus.ExodusDatabase,
    t::Type{Exodus.NodalVectorVariable},
    timestep::Integer,
    base_name::String
) -> Any

```

Wrapper method for nodal vector variables
