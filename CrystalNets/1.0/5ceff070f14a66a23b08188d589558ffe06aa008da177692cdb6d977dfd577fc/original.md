```
one_topology(itr::InterpenetratedTopologyResult, clustering::Union{Nothing,_Clustering}=nothing)
```

Return the only topology corresponding to the given clustering. If no clustering is given, return the only topology of the result.

If several topologies are found, return `nothing`.

If the clustering is not found in one of the interpenetrated topologies, return `missing`.
