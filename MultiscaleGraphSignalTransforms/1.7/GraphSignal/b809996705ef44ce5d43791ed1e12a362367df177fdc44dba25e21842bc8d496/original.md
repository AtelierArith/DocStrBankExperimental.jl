```
function ggrid(Nx::Int, Ny::Int, connect::Symbol)
```

Generate a GraphSig object for a 2-D grid that is `Nx` by `Ny`.

### Input Arguments

  * `Nx::Int`: the number of points in the x direction
  * `Ny::Int`: the number of points in the y direction
  * `connect::Symbol`: specifies the connectivity mode of the 2-D grid:   choices are: :c4 (default), :c8, :full

### Output Argument

  * `G::GraphSig`: the GraphSig ojbect representing the 2-D `Nx` by `Ny` grid.
