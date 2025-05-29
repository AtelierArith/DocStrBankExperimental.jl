```
EEquivGraphConv(in_dim=>out_dim, pos_dim, edge_dim; init=glorot_uniform)
```

E(n)-equivariant graph neural network layer.

# Arguments

  * `in_dim::Int`: node feature dimension. Data is assumed to be of the form [feature; coordinate], so `in_dim` must strictly be less than the dimension of the input vectors.
  * `out_dim`: the output of the layer will have dimension `out_dim` + (dimension of input vector - `in_dim`).
  * `hidden_dim::Int`: dimension of positional encoding.
  * `edge_dim::Int`: dimension of edge feature.
  * `init`: neural network initialization function.

# Examples

```jldoctest
julia> in_dim, out_dim, pos_dim = 3, 5, 2
(3, 5, 2)

julia> egnn = EEquivGraphConv(in_dim=>out_dim, pos_dim, in_dim)
EEquivGraphConv(ϕ_edge=Chain(Dense(10 => 2), Dense(2 => 2)), ϕ_x=Chain(Dense(2 => 2), Dense(2 => 1; bias=false)), ϕ_h=Chain(Dense(5 => 2), Dense(2 => 5)))
```

See also [`WithGraph`](@ref) for training layer with static graph and [`EEquivGraphPE`](@ref) for positional encoding.
