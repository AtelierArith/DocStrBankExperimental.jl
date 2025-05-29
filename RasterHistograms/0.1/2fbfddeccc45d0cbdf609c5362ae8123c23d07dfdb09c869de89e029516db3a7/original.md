```
function area_weights(rs::Union{Raster, RasterStack}; equator_one_degree = 111e3)
```

Return the `Weights` for a `Histogram` calculated from the area of each grid cell in a `Raster` or `RasterStack`. The `Raster` or `RasterStack` must first be sliced over the dimensions one wishes to look at, e.g. for area weights at sea surface the function need `rs[Z(1)]` to be passed in. If the original `Raster` only has two spatial dimensions then this step may be skipped. The keyword argument `equator_one_degree` is one degree at the equator in metres. The function returns a container `Weights` so can be passed straight into the `fit(::Histogram)` function.
