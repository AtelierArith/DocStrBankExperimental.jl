```julia
read_names(
    exo::Exodus.ExodusDatabase,
    _::Type{V<:Exodus.AbstractExodusVariable}
) -> Vector{String}

```

与えられた変数型 V の変数名を読み取る一般的なメソッド。

例: julia> read*names(exo, ElementVariable) "stress*xx" "stress*yy" "stress*zz" "stress*xy" "stress*yz" "stress_zx"

julia> read*names(exo, GlobalVariable) "global*displ" "reaction_force"

julia> read*names(exo, NodalVariable) "displ*x" "displ*y" "displ*z"

julia> read*name(exo, NodeSetVariable) "nset*displ*x" "nset*displ*y" "nset*displ_z"

julia> read_name(exo, SideSetVariable) "pressure"
