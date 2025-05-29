```
EdgeConv(nn; aggr=max)
```

Edge convolutional layer.

# Arguments

  * `nn`: A neural network (e.g. a Dense layer or a MLP).
  * `aggr`: An aggregate function applied to the result of message function.

`+`, `max` and `mean` are available.

# Examples

```jldoctest
julia> EdgeConv(Dense(1024, 256, relu))
EdgeConv(Dense(1024 => 256, relu), aggr=max)

julia> EdgeConv(Dense(1024, 256, relu), aggr=+)
EdgeConv(Dense(1024 => 256, relu), aggr=+)
```

See also [`WithGraph`](@ref) for training layer with static graph.
