```
    OrientationConvention(; compass_direction::AbstractChar = 'S', is_clockwise::Bool = false, in_radians = true, tol = sqrt(eps(Float64)))
```

Specifies the coordinate system context for `detect_gradient_orientation` which determines the meaning of the angles (the gradient orientations).

# Details

You can specify how you want the gradient orientation to be reported.  By default, the orientation is measured counter-clockwise from the south direction. This is because in a Raster coordinate system, the first spatial dimension increases as one goes down the image (i.e. it points south), and the second spatial dimension increases as one moves to the right of the image (i.e. it points east).

If you wish to interpret the orientation in a canonical Cartesian coordinate convention you would specify east as the reference compass direction (`compass_direction = 'E'`) and a counter-clockwise direction (`clockwise = false`).

If `in_radians = true` the valid angles are reported in the range of `[0...2π)`, otherwise they are reported in the range `[0...360)`. The values `2π` and `360` are used as sentinels to designate undefined angles (because the gradient magnitude was too close to zero). By default, an angle is undefined if `(abs(g₁) < tol && abs(g₂) < tol)` where `g₁` and `g₂` denote the gradient in the first and second spatial dimensions, and `tol = sqrt(eps(Float64))`.

# Example

```julia

using TestImages, FileIO, ImageView, ImageEdgeDetection, ImageFiltering

img =  testimage("mandril_gray")

# Gradient in the first and second spatial dimension
g₁, g₂ = imgradients(img, KernelFactors.scharr)

# Interpret the angles with respect to a canonical Cartesian coordinate system
# where the angles are measured counter-clockwise from the positive x-axis.

orientation_convention = OrientationConvention(in_radians = true,
                                               is_clockwise = false,
                                               compass_direction = 'E')
angles = detect_gradient_orientation(g₁, g₂, orientation_convention)

```
