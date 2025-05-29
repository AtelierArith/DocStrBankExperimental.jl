```
Spectral(; kwargs...)(adj_matrix)
spectral(adj_matrix; kwargs...)
```

This algorithm uses the technique of Spectral Graph Drawing. For reference see Koren (2003, [doi 10.1007/3-540-45071-8_50](https://doi.org/10.1007/3-540-45071-8_50)).

Takes adjacency matrix representation of a network and returns coordinates of the nodes.

## Keyword Arguments

  * `dim=3`, `Ptype=Float64`: Determines dimension and output type `Point{dim,Ptype}`.
  * `nodeweights=Float64[]`: Vector of weights. If network size does not match the length of `nodesize` use `ones` instead.
