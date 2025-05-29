```
make_graph(edges::AbstractVector)
```

`edges` からバスを推測して SimpleDiGraph を返します。バス => int および int => bus の辞書を使用します（Graphs.jl は整数ノードのみで動作するため）。

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
