```
imrotate(img, θ, [indices]; kwargs...) -> imgr
```

Rotate image `img` by `θ`∈[0,2π) in a clockwise direction around its center point.

# Arguments

  * `img::AbstractArray`: the original image that you need to rotate.
  * `θ::Real`: the rotation angle in clockwise direction. To rotate the image in conter-clockwise direction, use a negative value instead. To rotate the image by `d` degree, use the formular `θ=d*π/180`.
  * `indices` (Optional): specifies the output image axes. By default, rotated image `imgr` will not be cropped, and thus `axes(imgr) == axes(img)` does not hold in general.

# Parameters

!!! info
    To construct `method` and `fillvalue` values, you may need to load `Interpolations` package first.


  * `method::Union{Degree, InterpolationType}`: the interpolation method you want to use. By default it is `Linear()`.
  * `fillvalue`: the value that used to fill the new region. The default value is `NaN` if possible, otherwise is `0`.

This function is a simple high-level interface to `warp`, for more explaination and details, please refer to [`warp`](@ref).

# Examples

```julia
using TestImages, ImageTransformations
img = testimage("cameraman")

# Rotate the image by π/4 in the clockwise direction
imgr = imrotate(img, π/4) # output axes (-105:618, -105:618)

# Rotate the image by π/4 in the counter-clockwise direction
imgr = imrotate(img, -π/4) # output axes (-105:618, -105:618)

# Preserve the original axes
# Note that this is more efficient than `@view imrotate(img, π/4)[axes(img)...]`
imgr = imrotate(img, π/4, axes(img)) # output axes (1:512, 1:512)
```

By default, `imrotate` uses bilinear interpolation with constant fill value (`NaN` or `0`). You can, for example, use the nearest interpolation and fill the new region with white pixels:

```julia
using Interpolations, ImageCore
imrotate(img, π/4, method=Constant(), fillvalue=oneunit(eltype(img)))
```

And with some inspiration, maybe fill with periodic values and tile the output together to get a mosaic:

```julia
using Interpolations, ImageCore
imgr = imrotate(img, π/4, fillvalue = Periodic())
mosaicview([imgr for _ in 1:9]; nrow=3)
```
