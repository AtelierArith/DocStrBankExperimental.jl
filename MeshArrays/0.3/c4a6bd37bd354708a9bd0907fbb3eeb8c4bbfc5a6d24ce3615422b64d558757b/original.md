```
InterpolationFactors(Γ,lon::Array{T,1},lat::Array{T,1})
```

Compute interpolation coefficients etc from grid `Γ` to `lon,lat`

```jldoctest; output = false
using MeshArrays
γ=GridSpec("CubeSphere",MeshArrays.GRID_CS32)
Γ=GridLoad(γ; option="full")
lon=collect(45.:0.1:46.); lat=collect(60.:0.1:61.)
(f,i,j,w,j_f,j_x,j_y)=InterpolationFactors(Γ,lon,lat)
YC=Interpolate(Γ.YC,f,i,j,w)
extrema(i)==(9,10)

# output

true
```
