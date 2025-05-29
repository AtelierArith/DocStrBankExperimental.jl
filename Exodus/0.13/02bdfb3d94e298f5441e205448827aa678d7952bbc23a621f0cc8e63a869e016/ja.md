```julia
write_number_of_variables(
    exo::Exodus.ExodusDatabase,
    _::Type{V<:Exodus.AbstractExodusVariable},
    num_vars::Integer
)

```

与えられた変数タイプ V の変数の数を書くための一般的なメソッド。

例: julia> write*number*of_variables(exo, ElementVariable, 6)

julia> write*number*of_variables(exo, GlobalVariable, 5)

julia> write*number*of_variables(exo, NodalVariable, 3)

julia> write*number*of_variables(exo, NodeSetVariable, 3)

julia> write*number*of_variables(exo, SideSetVariable, 6)
