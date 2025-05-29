```
CGConv((node_dim, edge_dim), init, bias=true)
```

Crystal Graph Convolutional network. Uses both node and edge features.

# Arguments

  * `node_dim`: Dimensionality of the input node features. Also is necessarily the output dimensionality.
  * `edge_dim`: Dimensionality of the input edge features.
  * `init`: Initialization algorithm for each of the weight matrices
  * `bias`: Whether or not to learn an additive bias parameter.

# Examples

```jldoctest
julia> CGConv((128, 32))
CGConv(node dim=128, edge dim=32)
```

See also [`WithGraph`](@ref) for training layer with static graph.
