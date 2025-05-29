```julia
read_number_of_variables(
    exo::Exodus.ExodusDatabase,
    _::Type{V<:Exodus.AbstractExodusVariable}
) -> Int32

```

特定の変数タイプ V の変数の数を読み取る一般的なメソッド。

例: julia> read*number*of_variables(exo, ElementVariable) 6

julia> read*number*of_variables(exo, GlobalVariable) 5

julia> read*number*of_variables(exo, NodalVariable) 3

julia> read*number*of_variables(exo, NodeSetVariable) 3

julia> read*number*of_variables(exo, SideSetVariable) 6
