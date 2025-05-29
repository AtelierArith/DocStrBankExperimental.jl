```
struct MeshData{Dim, Tv, Ti}
```

MeshData: contains info for a high order piecewise polynomial discretization on an unstructured mesh. 

Example:

```julia
N, K1D = 3, 2
rd = RefElemData(Tri(), N)
VXY, EToV = uniform_mesh(Tri(), K1D)
md = MeshData(VXY, EToV, rd)
(; x, y ) = md
```
