```
shortest_path([PathAlgorithm,]
              g::OSMGraph,
              origin::Union{Integer,Node},
              destination::Union{Integer,Node},
              [weights::AbstractMatrix=g.weights;
              cost_adjustment::Function=(u, v, parents) -> 0.0),
              max_distance::W=typemax(W)]
```

Calculates the shortest path between two OpenStreetMap node ids.

# Arguments

  * `PathAlgorithm` (optional): Path finding algorithm, possible values are:

      * `Dijkstra`: Same as `DijkstraVector`. This is the default algorithm.
      * `DijkstraVector`: Dijkstra's algorithm using the `Vector` implementation.    Faster for small graphs and/or long paths.
      * `DijkstraDict`: Dijkstra's algorithm using the `Dict` implementation.   Faster for large graphs and/or short paths.
      * `AStar`: Same as `AStarVector`.
      * `AStarVector`: A* algorithm using the `Vector` implementation.   Faster for small graphs and/or long paths.
      * `AStarDict`: A* algorithm using the `Dict` implementation.   Faster for large graphs and/or short paths.
  * `g::OSMGraph{U,T,W}`: Graph container.
  * `origin::Union{Integer,Node}`: Origin OpenStreetMap node or node id.
  * `destination::Union{Integer,Node},`: Destination OpenStreetMap node or node    id.
  * `weights`: Optional matrix of node to node edge weights, defaults to    `g.weights`. If a custom weights matrix is being used with algorithm set to   `AStar`, make sure that a correct heuristic is being used.
  * `cost_adjustment::Function=(u,v,parents) -> 0.0`: Option to pass in a function    to adjust the cost between each pair of vetices `u` and `v`, normally the    cost is just the weight between `u` and `v`, `cost_adjustment` takes in 3    arguments; `u`, `v` and `parents`; to apply an additive cost to the default    weight. Defaults no adjustment. Use `restriction_cost_adjustment` to    consider turn restrictions.
  * `heuristic::Function=distance_heuristic(g)`: Use custom heuristic with the    `AStar` algorithms only. Defaults to a function    `h(u, v) -> haversine(u, v)`, i.e. returns the haversine distances between    `u`, the current node, and `v`, the neighbouring node. If `g.weight_type`    is `:time` or `:lane_efficiency`, use `time_heuristic(g)` instead.

# Return

  * `Union{Nothing,Vector{T}}`: Array of OpenStreetMap node ids making up    the shortest path.
