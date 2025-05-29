```julia
read_values(
    exo::Exodus.ExodusDatabase{M, I, B, F},
    _::Type{V<:Union{Exodus.NodeSetVariable, Exodus.SideSetVariable}},
    timestep::Integer,
    id::Integer,
    var_index::Integer
) -> Any

```

Method to read nodeset/sideset variables
