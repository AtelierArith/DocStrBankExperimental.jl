```julia
read_values(
    exo::Exodus.ExodusDatabase,
    _::Type{V<:Union{Exodus.ElementVariable, Exodus.NodalVariable, Exodus.NodeSetVariable, Exodus.SideSetVariable}},
    time_step::Integer,
    id::Integer,
    var_name::String
) -> Any

```
