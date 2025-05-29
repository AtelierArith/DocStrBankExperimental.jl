```
DataDiGraph{T,VL,VD,ED,GD} <: AbstractDataGraph{T}
```

Structure for graphs with metadata based on adjacency list storage.

# Fields

  * `ne::Int`: number of edges
  * `fadjlist::Vector{Vector{Int}}`: forward adjacency lists
  * `badjlist::Vector{Vector{Int}}`: backward adjacency lists
  * `labels::Vector{VL}`: list of vertex labels
  * `vertices::Dict{VL,T}`: dictionary mapping each vertex label to the associated integer index `v`
  * `vertex_data::Vector{VD}`: list of vertex data objects, indexed by integers `v`
  * `edge_data::Vector{Vector{ED}}`: list of edge data objects, indexed by `s` first and `d_index` second, where `d_index` is the rank of `d` among the outneighbors of `s`
  * `graph_data::GD`: single graph data object
