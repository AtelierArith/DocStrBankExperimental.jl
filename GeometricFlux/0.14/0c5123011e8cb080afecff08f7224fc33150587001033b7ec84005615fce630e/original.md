```
GINConv(nn, [eps=0])

Graph Isomorphism Network.
```

# Arguments

  * `nn`: A neural network/layer.
  * `eps`: Weighting factor.

# Examples

```jldoctest
julia> GINConv(Dense(1024, 256, relu))
GINConv(Dense(1024 => 256, relu), ϵ=0.0)

julia> GINConv(Dense(1024, 256, relu), 1.f-6)
GINConv(Dense(1024 => 256, relu), ϵ=1.0e-6)
```

See also [`WithGraph`](@ref) for training layer with static graph.
