Container for storing OpenStreetMap node, way, relation and graph related obejcts.

# Fields

`U <: Integer,T <: Union{String, Int},W <: Real`

  * `nodes::Dict{T,Node{T}}`: Mapping of node ids to node objects.
  * `node_coordinates::Vector{Vector{W}}`: Vector of node coordinates [[lat, lon]...], indexed by graph vertices.
  * `ways::Dict{T,Way{T}}`: Mapping of way ids to way objects. Previously called `highways`.
  * `node_to_index::OrderedDict{T,U}`: Mapping of node ids to graph vertices.
  * `index_to_node::OrderedDict{U,T}`: Mapping of graph vertices to node ids.
  * `node_to_way::Dict{T,Vector{T}}`: Mapping of node ids to vector of way ids. Previously called `node_to_highway`.
  * `edge_to_way::Dict{Vector{T},T}`: Mapping of edges (adjacent node pairs) to way ids. Previously called `edge_to_highway`.
  * `restrictions::Dict{T,Restriction{T}}`: Mapping of relation ids to restriction objects.
  * `indexed_restrictions::Union{DefaultDict{U,Vector{MutableLinkedList{U}}},Nothing}`: Mapping of via node ids to ordered sequences of restricted node ids.
  * `graph::Union{AbstractGraph,Nothing}`: Either DiGraph, StaticDiGraph, SimpleWeightedDiGraph or MetaDiGraph.
  * `weights::Union{SparseMatrixCSC{W,U},Nothing}`: Sparse adjacency matrix (weights between graph vertices), either `:distance` (km), `:time` (hours) or `:lane_efficiency` (time scaled by number of lanes).
  * `dijkstra_states::Vector{Vector{U}}`: Vector of dijkstra parent states indexed by source vertices, used to retrieve shortest path from source vertex to any other vertex.
  * `kdtree::Union{KDTree,Nothing}`: KDTree used to calculate nearest nodes.
  * `kdtree::Union{RTree,Nothing}`: R-tree used to calculate nearest nodes.
  * `weight_type::Union{Symbol,Nothing}`: Either `:distance`, `:time` or `:lane_efficiency`.
