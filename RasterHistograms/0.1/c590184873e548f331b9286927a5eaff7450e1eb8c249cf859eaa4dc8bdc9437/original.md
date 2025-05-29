```
function volume_weights(rs::Union{Raster, RasterStack}; equator_one_degree = 111e3)
```

Return the `Weights` for a `Histogram` calculated from the volume of each grid cell in a `Raster` or `RasterStack`. The model resolution is inferred from the `X` and `Y` dimensions of the `Raster` or `RasterStack` and assumes that along the `X` and `Y` the resolution is unique (though it can be different for `X` and `Y`). The keyword argument `equator_one_degree` is one degree at the equator in metres. The function returns a container `Weights` so can be passed straight into the `fit(::Histogram)` function.
