```
function depth_to_pressure(raster::Raster)
function depth_to_pressure(stack::RasterStack)
```

Convert the depth dimension (`Z`) to pressure using `gsw_p_from_z`  from GibbsSeaWater.jl. Note that pressure depends on depth and *latitude* so the returned pressure is stored as a variable in the resulting `Raster` rather than replacing the vertical depth dimension.
