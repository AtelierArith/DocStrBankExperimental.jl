```julia
write_values(
    exo::Exodus.ExodusDatabase,
    t::Type{Exodus.NodalVariable},
    timestep::Integer,
    var_index::Integer,
    var_values::Vector{<:AbstractFloat}
)

```

Wrapper for writing nodal variables by index number
