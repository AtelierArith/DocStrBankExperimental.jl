```
osm_subgraph(g::OSMGraph{U, T, W},
             vertex_list::Vector{U}
             )::OSMGraph where {U <: DEFAULT_OSM_INDEX_TYPE, T <: DEFAULT_OSM_ID_TYPE, W <: Real}
```

Create an OSMGraph representing a subgraph of another OSMGraph containing  specified vertices. The resulting OSMGraph object will also contain vertices from all ways that the specified vertices (nodes) are members of. Vertex numbers within the original graph object are not mapped to the subgraph.
