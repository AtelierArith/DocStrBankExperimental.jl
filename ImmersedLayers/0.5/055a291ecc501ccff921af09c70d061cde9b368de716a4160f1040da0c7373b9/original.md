```
SurfaceScalarCache(g::PhysicalGrid[,scaling=IndexScaling])
```

Create a cache of type `BasicILMCache` with scalar grid data, using the grid specified in `g`, with no immersed points. The keyword `scaling` can be used to set the scaling in the operations. By default, it is set to `IndexScaling` which sets the differential operators to be only differencing operators. By using `scaling = GridScaling`, then the grid and  spacings are accounted for and differential operators are scaled by this spacing.  The keyword `phys_params` can be used to supply physical parameters.
