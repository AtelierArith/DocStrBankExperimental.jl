```
agriculture(src::AbstractSatellite; lower=0.02, upper=0.98)
agriculture(s::Type{AbstractSatellite}, raster::AbstractRasterStack; lower=0.02, upper=0.98)
```

Visualize a satellite image with the agricultural band combination, which is used for crop monitoring and emphasizes healthy vegetation.

Accepts either an `AbstractSatellite` or a combination of `Type{AbstractSatellite}` and `AbstractRasterStack`.

Returns an `Array` of either `RGB{N0f8}` or `Gray{N0f8}` elements.

# Keywords

  * `lower`: The lower percentile to use for adjusting the image histogram.
  * `upper`: The upper percentile to use for adjusting the image histogram.
