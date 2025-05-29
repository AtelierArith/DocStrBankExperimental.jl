```
addroute!(p, nodes::Dict{Int,T},
               route::Vector{Int};
               route_color::Union{String, Plots.RGB} ="0x000053",
               km::Bool=false,
               start_name="A", end_name="B",
               fontsize=15
               ) where T<:Union{OpenStreetMapX.LLA,OpenStreetMapX.ENU}
```

Adds a `route` to the plot `p` using the node information stored in `nodes`.

The first element from the list of nodes `route` will be annoted by `start_name` while the last will be annotated by `end_name`. The `km` parameter can be used to have a kilometer scale of the map instead of meters.

Returns an object that can be used for further plot updates.
