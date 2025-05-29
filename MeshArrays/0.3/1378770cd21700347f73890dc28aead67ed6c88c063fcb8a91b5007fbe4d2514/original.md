```
Interpolate(z_in::MeshArray,f,i,j,w)
```

```
using MeshArrays

γ=GridSpec("LatLonCap",MeshArrays.GRID_LLC90)
Γ=GridLoad(γ; option="full")

lon=[i for i=-179.5:1.0:179.5, j=-89.5:1.0:89.5]
lat=[j for i=-179.5:1.0:179.5, j=-89.5:1.0:89.5]
(f,i,j,w,j_f,j_x,j_y)=InterpolationFactors(Γ,vec(lon),vec(lat))
DD=Interpolate(Γ.Depth,f,i,j,w)

using CairoMakie
heatmap(vec(lon[:,1]),vec(lat[1,:]),DD,colorrange=(0.,6000.))
```
