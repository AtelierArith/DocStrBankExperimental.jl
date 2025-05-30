```
swir(src::AbstractSatellite; lower=0.02, upper=0.98)
swir(s::Type{AbstractSatellite}, raster::AbstractRasterStack; lower=0.02, upper=0.98)
```

Visualize a satellite image using the SWIR band combination, which emphasizes dense vegetation as dark green.

Accepts either an `AbstractSatellite` or a combination of `Type{AbstractSatellite}` and `AbstractRasterStack`.

Returns an `Array` of either `RGB{N0f8}` or `Gray{N0f8}` elements.

# Keywords

  * `lower`: The lower percentile to use for adjusting the image histogram.
  * `upper`: The upper percentile to use for adjusting the image histogram.
