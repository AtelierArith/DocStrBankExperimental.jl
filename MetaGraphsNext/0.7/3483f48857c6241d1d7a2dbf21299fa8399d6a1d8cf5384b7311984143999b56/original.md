```
MetaGraph{
    Code<:Integer,
    Graph<:AbstractGraph{Code},
    Label,
    VertexData,
    EdgeData,
    GraphData,
    WeightFunction,
    Weight
} <: AbstractGraph{Code}
```

A graph type with custom vertex labels containing vertex-, edge- and graph-level metadata.

Vertex labels have type `Label`, while vertex (resp. edge, resp. graph) metadata has type `VertexData` (resp. `EdgeData`, resp. `GraphData`). It is recommended not to set `Label` to an integer type, so as to avoid confusion between vertex labels (which do not change as the graph evolves) and vertex codes (which have type `Code<:Integer` and can change as the graph evolves).

# Fields

  * `graph::Graph`: underlying, data-less graph with vertex codes of type `Code`
  * `vertex_labels::Dict{Code,Label}`: dictionary mapping vertex codes to vertex labels
  * `vertex_properties::Dict{Label,Tuple{Code,VertexData}}`: dictionary mapping vertex labels to vertex codes & metadata
  * `edge_data::Dict{Tuple{Label,Label},EdgeData}`: dictionary mapping edge labels such as `(label_u, label_v)` to edge metadata
  * `graph_data::GraphData`: metadata for the graph object as a whole
  * `weight_function::WeightFunction`: function computing edge weight from edge metadata, its output must have the same type as `default_weight`
  * `default_weight::Weight`: default weight used when an edge doesn't exist
