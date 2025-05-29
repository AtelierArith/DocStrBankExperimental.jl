```julia
read_name(
    exo::Exodus.ExodusDatabase,
    _::Type{V<:Exodus.AbstractExodusVariable},
    var_index::Integer
) -> String

```

与えられた変数タイプ V のインデックス var_index にある変数の名前を読み取る一般的なメソッド。

例: julia> read*name(exo, ElementVariable, 1) "stress*xx"

julia> read*name(exo, GlobalVariable, 2) "reaction*force"

julia> read*name(exo, NodalVariable, 1) "displ*x"

julia> read*name(exo, NodeSetVariable, 1) "nset*displ_x"

julia> read_name(exo, SideSetVariable, 1) "pressure"
