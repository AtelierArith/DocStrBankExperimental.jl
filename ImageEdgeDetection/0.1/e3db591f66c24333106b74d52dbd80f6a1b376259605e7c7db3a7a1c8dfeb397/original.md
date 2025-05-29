```
detect_gradient_orientation(g₁::AbstractArray, g₂::AbstractArray, orientation_convention::OrientationConvention, args...; kwargs...)
```

Given the gradient in the first (`g₁`) and second (`g₂`) spatial dimensions, returns the gradient orientation, where the orientation is interpreted according to a supplied [`OrientationConvention`](@ref ImageEdgeDetection.OrientationConvention).

# Details

You can specify how you want the gradient orientation to be reported by supplying an [`OrientationConvention`](@ref ImageEdgeDetection.OrientationConvention). If left unspecified the orientation is measured counter-clockwise from the south direction. This is because in a Raster coordinate system, the first spatial dimension increases as one goes down the image (i.e. it points south), and the second spatial dimension increases as one moves to the right of the image (i.e. it points east).

If you wish to interpret the orientation in a canonical Cartesian coordinate convention you would specify east as the reference compass direction (`compass_direction = 'E'`) and a counter-clockwise direction (`clockwise = false`).

# Output

Returns a two-dimensional array of angles. If `in_radians = true` the valid angles are reported in the range of `[0...2π)`, otherwise they are reported in the range `[0...360)`. The values `2π` and `360` are used as sentinels to designate undefined angles (because the gradient magnitude was too close to zero). By default, an angle is undefined if `(abs(g₁) < tol && abs(g₂) < tol)` where `g₁` and `g₂` denote the gradient in the first and second spatial dimensions, and `tol = sqrt(eps(Float64))` (as defined in [`OrientationConvention`](@ref ImageEdgeDetection.OrientationConvention)).

See also: [`detect_gradient_orientation!`](@ref)
