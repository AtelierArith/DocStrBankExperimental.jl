```julia
read_name(
    exo::Exodus.ExodusDatabase,
    _::Type{V<:Exodus.AbstractExodusVariable},
    var_index::Integer
) -> String

```

General method to read the name of a variable in index var_index  for a given variable type V.

Examples: julia> read*name(exo, ElementVariable, 1) "stress*xx"

julia> read*name(exo, GlobalVariable, 2) "reaction*force"

julia> read*name(exo, NodalVariable, 1) "displ*x"

julia> read*name(exo, NodeSetVariable, 1) "nset*displ_x"

julia> read_name(exo, SideSetVariable, 1) "pressure"
