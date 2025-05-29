```
make_graph(busses::AbstractVector{String}, edges::AbstractVector)
```

バス => 整数および整数 => バスの辞書を持つSimpleDiGraphを返します（Graphs.jlは整数ノードのみで動作するため）。

```julia
julia> g["13", :bus]
10

julia> get_prop(g, :bus_int_map)["13"]
10

julia> g[13, :bus]
"24"

julia> get_prop(g, :int_bus_map)[13]
"24"
```
