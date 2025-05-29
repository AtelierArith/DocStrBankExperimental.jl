Basic structure for 2D meshes

```
Bmesh2D(etype::Symbol,nn::Int64,ne::Int64,coord::Matrix{Float64},connect::Matrix{Int64},
        Lx::Float64, Ly::Float64, nx::Int64, ny::Int64)
```

where:

```
etype   = :truss2D or :solid2D
nn      = number of nodes
ne      = number of elements
coord   = nn x 2 matrix with nodal coordinates (x y)
connect = ne x {2,4} matrix with element connectivities. 2 for :truss2D and 4 for :solid2D
Lx      = horizontal (X) length (if using a rectangular domain)
nx      = number of divisions (elements) in the horizontal direction 
Ly      = vectival (Y) length (if using a rectangular domain)
ny      = number of divisions (elements) in the vertical direction
```
