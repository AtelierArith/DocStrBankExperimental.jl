```
Buchheim(; kwargs...)(adj_matrix)
Buchheim(; kwargs...)(adj_list)
buchheim(adj_matrix; kwargs...)
buchheim(adj_list; kwargs...)
```

Using the algorithm proposed by Buchheim, Junger and Leipert (2002, [doi 10.1007/3-540-36151-0_32](https://doi.org/10.1007/3-540-36151-0_32)).

Takes adjacency matrix or list representation of given tree and returns coordinates of the nodes.

## Keyword Arguments

  * `Ptype=Float64`: Determines the output type `Point{2,Ptype}`.
  * `nodesize=Float64[]`

    Determines the size of each of the node. If network size does not match the length of `nodesize` fill up with `ones` or truncate given parameter.
