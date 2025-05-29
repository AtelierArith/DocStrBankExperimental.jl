```
PowerModelsGraph
    graph::Graphs.SimpleDiGraph
    node_comp_map::Dict{Int,Tuple{String, String}}
    edge_comp_map::Dict{Graphs.AbstractEdge,Tuple{String, String}}
    edge_connector_map::Dict{Graphs.AbstractEdge,Tuple{String, String}}
```

A structure containing a graph of a PowerModels or PowerModelsDistribution network with four fields: a Graphs.SimpleDiGraph, a map from the node ids to the components, and  a map from the edges to the components, and a map from the edges to conenctors.
