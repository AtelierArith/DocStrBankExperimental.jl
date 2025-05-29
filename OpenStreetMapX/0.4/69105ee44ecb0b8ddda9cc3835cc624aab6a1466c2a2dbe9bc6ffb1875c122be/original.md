```
get_distance(A::Int, B::Int, 
             nodes::Dict{Int,T} , 
             vertices_to_nodes::Vector{Int}) where T<:Union{OpenStreetMapX.ENU,OpenStreetMapX.ECEF}
```

Auxiliary function - takes two vertices of graph and return the distance between them.  Used to compute straight line distance heuristic for A* algorithm.

**Arguments**

  * `A` : start vertex
  * `B` : end vertex
  * `nodes` : dictionary of .osm nodes ID's and correspoding points coordinates
  * `vertices_to_nodes` : dictionary mapping graph vertices to .osm file nodes
