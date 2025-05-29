```
`powerplot!(
    plt_layer::VegaLite.VLSpec, case::Dict{String,<:Any};
    layout_algorithm=kamada_kawai,
    edge_components=[:branch],
    node_components=[:bus],
    connected_components=[:gen,:load],
    fixed=false,
    kwargs...)`
```

Create a plower plot, with a different VegaLite plot as the bottom layer of the plot.  Primarily used to plot geographic map data underneath a power grid.
