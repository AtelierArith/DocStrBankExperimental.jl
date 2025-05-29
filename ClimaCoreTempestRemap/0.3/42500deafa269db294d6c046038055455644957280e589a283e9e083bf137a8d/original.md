```
rll_mesh(filename::AbstractString; nlat=90, nlon = round(Int, nlat * 1.6); verbose=false)
```

Create a regular latitude-longitude (RLL) mesh and write it to `filename` in Exodus format. `nlat` is the number of latitudinal cells, and `nlon` is the number of longitudinal cells.

Set `verbose=true` to print information.

See [Tempest remap: mesh generation](https://github.com/ClimateGlobalChange/tempestremap/#mesh-generation)
