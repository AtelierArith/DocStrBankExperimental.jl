Generate a 2D background mesh for :truss2D elements

```
Bmesh_truss_2D(Lx::Float64, nx::Int64, Ly::Float64, ny::Int64)
```

where

```
Lx  = length in X (horizonal direction)
nx  = number of divisions (elements) in X
Ly  = lenght in Y (vertical direction)
ny  = number of divisions (elements) in Y
```

returns

```
Bmesh2D(:truss2D,nn,ne,coord,connect,Lx,Ly, nx,ny)
```

where

```
nn      = number of nodes 
ne      = number of elements
coord   = matrix nn x 2 with nodal coordinates (x y) 
connect = matrix ne x 2 with connectivities
```

Nodes are created from bottom left (0,0) to bottom right (0,Lx),row by row.  Horizontal elements are generated first, followed by vertical, diagonal / and then the other diagonals.
