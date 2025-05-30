```
visualize(g::AbstractRaster; lower=0.02, upper=0.98)
visualize(r::AbstractRaster, g::AbstractRaster, b::AbstractRaster; lower=0.02, upper=0.98)
```

Visualize an RGB or grayscale satellite image.

Returns an `Array` of either `RGB{N0f8}` or `Gray{N0f8}` elements.

# Keywords

  * `lower`: The lower percentile to use for adjusting the image histogram.
  * `upper`: The upper percentile to use for adjusting the image histogram.

# Example

```julia
using RemoteSensingToolbox, Rasters, FileIO

# Prepare a Landsat 8 Image
src = Landsat8("LC08_L2SP_043024_20200802_20200914_02_T1")

# Display True Color Image
r, g, b = RasterStack(src, [:red, :green, :blue])
img = visualize(r, g, b; upper=0.90)
FileIO.save("truecolor.jpg", img)
```
