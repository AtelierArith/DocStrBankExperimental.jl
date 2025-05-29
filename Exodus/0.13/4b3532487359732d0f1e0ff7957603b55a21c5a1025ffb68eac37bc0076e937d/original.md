```julia
write_values(
    exo::Exodus.ExodusDatabase,
    _::Type{V<:Exodus.AbstractExodusVariable},
    timestep::Integer,
    id::Integer,
    var_name::String,
    var_value::Vector{<:AbstractFloat}
)

```
