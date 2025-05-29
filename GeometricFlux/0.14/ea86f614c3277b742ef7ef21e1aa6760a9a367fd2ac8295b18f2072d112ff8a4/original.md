```
EEquivGraphPE(in_dim=>out_dim; init=glorot_uniform, bias=true)
```

E(n)-equivariant positional encoding layer.

# Arguments

  * `in_dim::Int`: dimension of input positional feature.
  * `out_dim::Int`:  dimension of output positional feature.
  * `init`: neural network initialization function.
  * `bias::Bool`: dimension of edge feature.

# Examples

```jldoctest
julia> in_dim_edge, out_dim = 2, 5
(2, 5)

julia> l = EEquivGraphPE(in_dim_edge=>out_dim)
EEquivGraphPE(2 => 5)
```

See also [`EEquivGraphConv`](@ref).
