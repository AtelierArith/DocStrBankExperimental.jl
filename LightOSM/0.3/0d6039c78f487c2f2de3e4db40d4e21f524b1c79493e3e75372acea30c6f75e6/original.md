```
shortest_path_from_dijkstra_state(g::OSMGraph, origin::Integer, destination::Integer)
```

Extract shortest path from precomputed dijkstra state, from `origin` to `detination` node id.

Note, function will raise `UndefRefError: access to undefined reference` if the dijkstra state of the origin node is not precomputed.

# Arguments

  * `g::OSMGraph`: Graph container.
  * `origin::Integer`: Origin OpenStreetMap node or node id.
  * `destination::Integer`: Destination OpenStreetMap node or node id.

# Return

  * `Union{Nothing,Vector{T}}`: Array of OpenStreetMap node ids making up the shortest path.
