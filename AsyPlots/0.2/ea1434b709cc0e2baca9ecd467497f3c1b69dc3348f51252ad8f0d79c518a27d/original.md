```
Surface(x::Array{<:Real},
        y::Array{<:Real},
        z::Array{<:Real,2};
        options)
Surface(z::Array{<:Real},2)
```

A graphics primitive representing a surface in three dimensions `x` and `y` may be one- or two-dimensional arrays

The surface passes through the points     [x[i,j],y[i,j],z[i,j] for i=1:size(z,1),j=1:size(z,2)]

The options are

  * `colors`: A vector of color names, for coloring
  * `spline`: whether to draw a smooth or piecewise smooth surface
  * `surfacepen`: a pen for drawing the surface
  * `meshpen`: a pen for drawing the grid lines on the surface
  * `clip`: either `false` or a boolean array of the same dimensions         as `x`, `y`, and `z`, specifying patches to exclude
