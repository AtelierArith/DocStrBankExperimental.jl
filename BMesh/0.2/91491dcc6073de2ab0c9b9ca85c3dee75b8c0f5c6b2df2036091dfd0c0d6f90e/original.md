Generate a 3D background mesh for truss:3D elements

```
Bmesh_truss_3D(Lx::Float64,nx::Int64,Ly::Float64,ny::Int64,Lz::Float64,nz::Int64)
```

where

```
Lx  = length in X (horizonal direction)
nx  = number of divisions (elements) in X
Ly  = length in Y (horizonal direction)
ny  = number of divisions (elements) in Y
Lz  = lenght in Z (vertical direction)
nz  = number of divisions (elements) in Z
```

returns

```
Bmesh3D(:truss3D,nn,ne,coord,connect,Lx,Ly,Lz,nx,ny,nz)
```

where

```
nn      = number of nodes 
ne      = number of elements
coord   = matrix nn x 3 with nodal coordinates (x y z) 
connect = matrix ne x 2 with connectivities.
```

Nodes are generated plane by plane, from z=0 to z=Lz.     Connectivities follow the same pattern.
