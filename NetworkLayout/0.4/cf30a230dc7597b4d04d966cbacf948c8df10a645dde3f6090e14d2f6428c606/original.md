```
Shell(; kwargs...)(adj_matrix)
shell(adj_matrix; kwargs...)
```

Position nodes in concentric circles. Without further arguments all nodes will be placed on a circle with radius 1.0. Specify placement of nodes using the `nlist` argument.

Takes adjacency matrix representation of a network and returns coordinates of the nodes.

## Keyword Arguments

  * `Ptype=Float64`: Determines the output type `Point{2,Ptype}`.
  * `nlist=Vector{Int}[]`

    Vector of Vector of node indices. Tells the algorithm, which nodes to place on which shell from inner to outer. Nodes which are not present in this list will be place on additional outermost shell.

This function started as a copy from [IainNZ](https://github.com/IainNZ)'s [GraphLayout.jl](https://github.com/IainNZ/GraphLayout.jl)
