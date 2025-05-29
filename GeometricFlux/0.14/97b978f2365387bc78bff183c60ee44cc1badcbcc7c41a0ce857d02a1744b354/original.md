```
GCNConv(in => out, σ=identity; bias=true, init=glorot_uniform)
```

Graph convolutional layer. The input to the layer is a node feature array `X` of size `(num_features, num_nodes)`.

# Arguments

  * `in`: The dimension of input features.
  * `out`: The dimension of output features.
  * `σ`: Activation function.
  * `bias`: Add learnable bias.
  * `init`: Weights' initializer.

# Examples

```jldoctest
julia> gc = GCNConv(1024=>256, relu)
GCNConv(1024 => 256, relu)
```

See also [`WithGraph`](@ref) for training layer with static graph.
