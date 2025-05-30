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
L=(lon=lon, lat=lat, f=f, i=i, j=j, w=w)

using CairoMakie
heatmap(Interpolate(Γ.Depth,L)...,colorrange=(0.,6000.))
```

または 

```
heatmap(Γ.Depth,interpolation=L,colorrange=(0.,6000.))
```
