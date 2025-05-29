Generate a 2D background mesh for 4-node solid (planar) elements (:solid2D)

```
Bmesh_solid_2D(Lx::Float64, nx::Int64, Ly::Float64, ny::Int64)
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
Bmesh2D(:solid2D,nn,ne,coord,connect,Lx,Ly, nx,ny)
```

where

```
nn      = number of nodes 
ne      = number of elements
coord   = matrix nn x 2 with nodal coordinates (x y) 
connect = matrix ne x 4 with connectivities
```
