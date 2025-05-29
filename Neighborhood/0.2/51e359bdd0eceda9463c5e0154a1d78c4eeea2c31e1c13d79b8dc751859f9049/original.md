```
searchstructure(S, data, metric; kwargs...) → ss
```

Create a search structure `ss` of type `S` (e.g. `KDTree, BKTree, VPTree` etc.) based on the given `data` and `metric`. The data types and supported metric types are package-specific, but typical choices are subtypes of `<:Metric` from Distances.jl. Some common metrics are re-exported by Neighborhood.jl.
