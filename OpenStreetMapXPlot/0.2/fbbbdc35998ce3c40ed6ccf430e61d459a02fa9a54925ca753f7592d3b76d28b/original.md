```
plot_nodes!(p, m::OpenStreetMapX.MapData,
    nodeids::Vector{Int};
    start_numbering_from::Union{Int,Nothing}=1,
    km::Bool=false,
    color="darkgreen",
    fontsize=10)
```

Plots nodes having node identifiers `nodeids` on the plot `p` using map information `m`. By default the node indices within the are plotted (e.g. 1, 2, 3...), however, setting the parameter `start_numbering_from` to nothing will show actual OSM node identifiers. The `km` parameter can be used to have a kilometer scale of the map instead of meters.

Returns an object that can be used for further plot updates.
