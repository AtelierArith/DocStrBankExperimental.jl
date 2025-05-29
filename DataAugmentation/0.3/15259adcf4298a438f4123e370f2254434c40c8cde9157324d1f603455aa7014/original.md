```
Image(image[, bounds]; interpolate=BSpline(Linear()), extrapolate=zero(T))
```

Item representing an N-dimensional image with element type T. Optionally, the interpolation and extrapolation method can be provided. Interpolation here refers to how the values of projected pixels that fall into the transformed content bounds are calculated. Extrapolation refers to how to assign values that fall outside the projected content bounds. The default is linear interpolation and to fill new regions with zero.

!!! info
    The `Interpolations` package provides numerous methods for use with the `interpolate` and `extrapolate` keyword arguments.  For instance, `BSpline(Linear())` and `BSpline(Constant())` provide linear and nearest neighbor interpolation, respectively. In addition `Flat()`, `Reflect()` and `Periodic()` boundary conditions are available for extrapolation.


## Examples

```julia
using DataAugmentation, Images

imagedata = rand(RGB, 100, 100)
item = Image(imagedata)
showitems(item)
```

If `T` is not a color, the image will be interpreted as grayscale:

```julia
imagedata = rand(Float32, 100, 100)
item = Image(imagedata)
showitems(item)
```
