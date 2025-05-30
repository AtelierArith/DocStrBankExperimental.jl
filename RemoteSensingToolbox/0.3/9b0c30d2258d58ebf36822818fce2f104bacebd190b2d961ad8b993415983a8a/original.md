```
true_color(src::AbstractSatellite; lower=0.02, upper=0.98)
true_color(s::Type{AbstractSatellite}, raster::AbstractRasterStack; lower=0.02, upper=0.98)
```

Visualize a satellite image using the true-color band combination, which appears like a natural image.

Accepts either an `AbstractSatellite` or a combination of `Type{AbstractSatellite}` and `AbstractRasterStack`.

Returns an `Array` of either `RGB{N0f8}` or `Gray{N0f8}` elements.

# Keywords

  * `lower`: The lower percentile to use for adjusting the image histogram.
  * `upper`: The upper percentile to use for adjusting the image histogram.

# Example

```julia
using RemoteSensingToolbox, Rasters

# Prepare a Landsat 8 Image
src = Landsat8("LC08_L2SP_043024_20200802_20200914_02_T1")

# Read Bands Directly from Disk
true_color(src; upper=0.90)

# Read Bands from a RasterStack
stack = RasterStack(src; lazy=true)
true_color(Landsat8, stack; upper=0.90)
```
