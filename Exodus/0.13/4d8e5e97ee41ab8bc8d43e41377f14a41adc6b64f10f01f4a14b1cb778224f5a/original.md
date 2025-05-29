```julia
read_values(
    exo::Exodus.ExodusDatabase{M, I, B, F},
    _::Type{V<:Exodus.NodalVariable},
    timestep::Integer,
    id::Integer,
    var_index::Integer
) -> Any

```

Method to read nodal variables
