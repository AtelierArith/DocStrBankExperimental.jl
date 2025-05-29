```
`powerplot(
    case::Dict{String,<:Any};
    layout_algorithm=kamada_kawai,
    edge_components=[:branch],
    node_components=[:bus],
    connected_components=[:gen,:load],
    fixed=false,
    kwargs...)`
```

Create a plower plot. Check github repo for documentation on kwarg options.
