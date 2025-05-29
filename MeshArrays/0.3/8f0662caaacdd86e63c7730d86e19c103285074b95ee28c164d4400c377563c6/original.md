```
gridpath
```

gridpath data structure.

```
using MeshArrays
γ=GridSpec("LatLonCap",MeshArrays.GRID_LLC90)
Γ=GridLoad(γ;option="light")
lons=[-68 -63]; lats=[-54 -66]; name="Drake Passage"
Trsct=Transect(name,lons,lats,Γ)
```
