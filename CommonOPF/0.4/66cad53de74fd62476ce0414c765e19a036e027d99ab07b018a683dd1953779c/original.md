```
make_graph(edges::AbstractVector{<:AbstractEdge};  directed::Union{Bool,Missing}=missing)
```

return MetaGraph made up of the `edges`

Also the graph[:int*bus*map] is created with the dicts for bus => int and int => bus (because Graphs.jl only works with integer nodes)

```julia
julia> g["13", :bus]
10

julia> g[13, :bus]
"24"

julia> get_prop(g, :int_bus_map)[13]
"24"
```
