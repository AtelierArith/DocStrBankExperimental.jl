```
GraphParallel(; node_layer=identity, edge_layer=identity, global_layer=identity,
                positional_layer=identity)
```

Passing features in `FeaturedGraph` in parallel. It takes `FeaturedGraph` as input and it can be specified by assigning layers for specific (node, edge and global) features.

# Arguments

  * `node_layer`: A regular Flux layer for passing node features.
  * `edge_layer`: A regular Flux layer for passing edge features.
  * `global_layer`: A regular Flux layer for passing global features.
  * `positional_layer`: A regular Flux layer for passing positional features.

# Example

```jldoctest
julia> using Flux, GeometricFlux

julia> l = GraphParallel(
            node_layer=Dropout(0.5),
            global_layer=Dense(10, 5)
       )
GraphParallel(node_layer=Dropout(0.5), edge_layer=identity, global_layer=Dense(10 => 5), positional_layer=identity)
```
