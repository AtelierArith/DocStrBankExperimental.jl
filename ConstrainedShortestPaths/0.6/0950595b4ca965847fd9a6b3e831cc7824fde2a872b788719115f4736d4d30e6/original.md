```julia
struct CSPInstance{T, G<:Graphs.AbstractGraph{T}, FR, BR, C, FF<:(AbstractMatrix), BF<:(AbstractMatrix)} <: ConstrainedShortestPaths.AbstractCSPInstance
```

# Fields

  * `graph::Graphs.AbstractGraph`: acyclic digraph in which to compute the shortest path
  * `origin_vertex::Any`: origin vertex of path
  * `destination_vertex::Any`: destination vertex of path
  * `origin_forward_resource::Any`: forward resource at the origin vertex
  * `destination_backward_resource::Any`: backward resource at the destination vertex
  * `cost_function::Any`: cost function
  * `forward_functions::AbstractMatrix`: forward functions along edges
  * `backward_functions::AbstractMatrix`: backward functions along edges
  * `is_useful::BitVector`: bit vector indicating if a vertices will be useful in the path computation, i.e. if there is a path from origin to destination that goes through it
  * `topological_ordering::Vector`: precomputed topological ordering of useful vertices, from destination to source
