```
SquareGrid(; kwargs...)(adj_matrix)
squaregrid(adj_matrix; kwargs...)
```

Position nodes on a 2 dimensional rectagular grid. The nodes are placed in order from upper left to lower right. To skip positions see `skip` argument.

Takes adjacency matrix representation of a network and returns coordinates of the nodes.

## Keyword Arguments

  * `Ptype=Float64`: Determines the output type `Point{2,Ptype}`
  * `cols=:auto`: Columns of the grid, the rows are determined automatic. If `:auto` the layout will be square-ish.
  * `dx=Ptype(1), dy=Ptype(-1)`: Ofsets between rows/cols.
  * `skip=Tuple{Int,Int}[]`: Specify positions to skip when placing nodes. `skip=[(i,j)]` means to keep the position in the `i`-th row and `j`-th column empty.
