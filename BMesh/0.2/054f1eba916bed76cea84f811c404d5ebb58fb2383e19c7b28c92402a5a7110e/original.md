Basic structure for 3D meshes

```
Bmesh3D(etype::Symbol,nn::Int64,ne::Int64,coord::Matrix{Float64},connect::Matrix{Int64},
        Lx::Float64, Ly::Float64, Lz::Float64,nx::Int64, ny::Int64, nz::Int64)
```

where:

```
etype   = :truss2D or :solid2D
nn      = number of nodes
ne      = number of elements
coord   = nn x 3 matrix with nodal coordinates (x y z)
connect = ne x {2,8} matrix with element connectivities. 2 for :truss3D and 8 for :solid3D
Lx      = horizontal (X) length (if using a cubic domain)
nx      = number of divisions (elements) in the horizontal X direction 
Ly      = horizontal (Y) length (if using a cubic domain)
ny      = number of divisions (elements) in the horizontal Y direction 
Lz      = vertical (Z) length (if using a cubic domain)
nz      = number of divisions (elements) in the vertical direction
```
