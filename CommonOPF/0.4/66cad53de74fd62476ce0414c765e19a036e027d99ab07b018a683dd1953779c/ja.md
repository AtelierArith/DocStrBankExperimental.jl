```
make_graph(edges::AbstractVector{<:AbstractEdge};  directed::Union{Bool,Missing}=missing)
```

`edges`から構成されるMetaGraphを返します。

また、graph[:int*bus*map]は、バス => 整数および整数 => バスの辞書を使用して作成されます（Graphs.jlは整数ノードのみで動作するため）。

```julia
julia> g["13", :bus]
10

julia> g[13, :bus]
"24"

julia> get_prop(g, :int_bus_map)[13]
"24"
```
