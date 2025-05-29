```
gcmgrid
```

gcmgrid data structure. Available constructors:

```
gcmgrid(path::String, class::String, nFaces::Int, 
        fSize::Array{NTuple{2, Int},1},
        ioSize::Union{NTuple{2, Int},Array{Int64,2}},
        ioPrec::Type, read::Function, write::Function)
```

The `class` can be set to "LatLonCap", "CubeSphere", "PeriodicChannel", "PeriodicDomain".

For example, A periodic channel (periodic in the x direction) of size 360 by 160, can be defined as follows.

```
pth=MeshArrays.GRID_LL360
class="PeriodicChannel"
ioSize=(360, 160)
ioPrec=Float32

γ=gcmgrid(pth, class, 1, [ioSize], ioSize, ioPrec, read, write)

Γ=GridLoad(γ)    
```

Please refer to `GridSpec` and `UnitGrid` for more info related to `gcmgrid` options.
