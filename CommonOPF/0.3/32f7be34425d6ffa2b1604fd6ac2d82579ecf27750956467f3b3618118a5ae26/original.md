```
make_graph(edges::AbstractVector)
```

return SimpleDiGraph by inferring busses from `edges` with the dicts for bus => int and int => bus (because Graphs.jl only works with integer nodes)

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
