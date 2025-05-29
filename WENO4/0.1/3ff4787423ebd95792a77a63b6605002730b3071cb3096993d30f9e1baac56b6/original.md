```
function interpolate_weno4(
    xs::AbstractVector{<:Number},
    xp::AbstractVector{<:Number},
    fp::AbstractVector{<:Number};
    extrapolate=false
)
```

Performs 1D interpolation using the fourth-order Weighted Essentially Non-Oscillatory (WENO) scheme from [Janett et al (2019)](https://ui.adsabs.harvard.edu/abs/2019A%26A...624A.104J/abstract). Based on https://github.com/Goobley/Weno4Interpolation by Chris Osborne.

# Arguments

  * `xs::AbstractVector{<:Number}`: The x-coordinates at which to evaluate the interpolated values
  * `xp::AbstractVector{<:Number}`: The x-coordinates of the data points. Must have at least four elements, be increasing, and have no NaNs.
  * `fp::AbstractVector{<:Number}`: The y-coordinates of the data points. Must have same length as `xp`.

# Keywords

  * `extrapolate::Bool`: whether or not to use extrapolation. If `true`, will perform quadratic extrapolation from the edge points. When `false`, it will not throw an error if `xs` is outside `xp`, but return the closest `fp` value.
