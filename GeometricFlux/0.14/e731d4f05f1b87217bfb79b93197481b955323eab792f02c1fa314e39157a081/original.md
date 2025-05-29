```
GraphConv(in => out, σ=identity, aggr=+; bias=true, init=glorot_uniform)
```

Graph neural network layer.

# Arguments

  * `in`: The dimension of input features.
  * `out`: The dimension of output features.
  * `σ`: Activation function.
  * `aggr`: An aggregate function applied to the result of message function. `+`, `-`,

`*`, `/`, `max`, `min` and `mean` are available.

  * `bias`: Add learnable bias.
  * `init`: Weights' initializer.

# Examples

```jldoctest
julia> GraphConv(1024=>256, relu)
GraphConv(1024 => 256, relu, aggr=+)

julia> GraphConv(1024=>256, relu, *)
GraphConv(1024 => 256, relu, aggr=*)
```

See also [`WithGraph`](@ref) for training layer with static graph.
