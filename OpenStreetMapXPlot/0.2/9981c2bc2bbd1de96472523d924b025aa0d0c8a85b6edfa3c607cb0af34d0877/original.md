```
addroute!(p, m::OpenStreetMapX.MapData,
               route::Vector{OpenStreetMapX.LLA};
               route_color::Union{String, Plots.RGB} ="0x000053",
               km::Bool=false,
               start_name="A", end_name="B",
               fontsize=15
               )
```

Adds a `route` in LLA coordinates to the plot `p` representing the map `m`.

The first element from the list of route coordinates `route` will be annoted by `start_name` while the last will be annotated by `end_name`. The `km` parameter can be used to have a kilometer scale of the map instead of meters.

Returns an object that can be used for further plot updates.
