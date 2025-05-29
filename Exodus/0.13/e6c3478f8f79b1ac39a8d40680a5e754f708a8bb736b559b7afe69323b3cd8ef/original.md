```julia
write_values(
    exo::Exodus.ExodusDatabase,
    t::Type{Exodus.NodalVariable},
    timestep::Integer,
    var_name::String,
    var_values::Vector{<:AbstractFloat}
)

```

Wrapper method for nodal variables
