```
node_identifier([T], g, dims...; method=GraphSignals.orthogonal_random_features)
```

Constructing node identifier for a graph `g` with additional dimensions `dims`.

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

julia> adjm = [0 1 1 1;
               1 0 1 0;
               1 1 0 1;
               1 0 1 0];

julia> batch_size = 10
10

julia> node_id = node_identifier(adjm, batch_size; method=GraphSignals.orthogonal_random_features);

julia> size(node_id)
(4, 4, 10)
```

See also [`identifiers`](@ref) for node/edge identifiers.
