```
identifiers([T], g, dims...; method=orthogonal_random_features)
```

Returns node identifier and edge identifier.

# Arguments

  * `T`: Element type of returning objects.
  * `g`: Data representing the graph topology. Possible type are

      * An adjacency matrix.
      * An adjacency list.
      * A Graphs' graph, i.e. `SimpleGraph`, `SimpleDiGraph` from Graphs, or `SimpleWeightedGraph`,   `SimpleWeightedDiGraph` from SimpleWeightedGraphs.
      * An `AbstractFeaturedGraph` object.
  * `dims`: Additional dimensions desired following after first two dimensions.
  * `method`: Available methods are `GraphSignals.orthogonal_random_features` and   `GraphSignals.laplacian_matrix`.

# Usage

```jldoctest
julia> using GraphSignals

julia> V, E = 4, 5
(4, 5)

julia> batch_size = 10
10

julia> adjm = [0 1 1 1;
               1 0 1 0;
               1 1 0 1;
               1 0 1 0];

julia> node_id, edge_token = identifiers(adjm, batch_size);

julia> size(node_id)
(8, 4, 10)

julia> size(edge_id)
(8, 10, 10)
```

See also [`node_identifier`](@ref) for generating node identifier only.
