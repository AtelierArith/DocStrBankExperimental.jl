```julia
write_values(
    exo::Exodus.ExodusDatabase,
    _::Type{V<:Exodus.AbstractExodusVariable},
    timestep::Integer,
    id::Integer,
    var_index::Integer,
    var_values::Vector{<:AbstractFloat}
)

```
