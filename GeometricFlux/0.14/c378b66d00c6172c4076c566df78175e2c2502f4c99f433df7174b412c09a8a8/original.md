```
GatedGraphConv([fg,] out, num_layers; aggr=+, init=glorot_uniform)
```

Gated graph convolution layer.

# Arguments

  * `out`: The dimension of output features.
  * `num_layers`: The number of gated recurrent unit.
  * `aggr`: An aggregate function applied to the result of message function. `+`, `-`,

`*`, `/`, `max`, `min` and `mean` are available.

# Examples

```jldoctest
julia> GatedGraphConv(256, 4)
GatedGraphConv((256 => 256)^4, aggr=+)

julia> GatedGraphConv(256, 4, aggr=*)
GatedGraphConv((256 => 256)^4, aggr=*)
```

See also [`WithGraph`](@ref) for training layer with static graph.
