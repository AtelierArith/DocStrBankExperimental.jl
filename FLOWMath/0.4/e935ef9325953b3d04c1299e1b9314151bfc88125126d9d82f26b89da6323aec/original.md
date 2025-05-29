```
linear(xdata, ydata, x::Number)
```

Linear interpolation.

**Arguments**

  * `xdata::Vector{Float64}`: x data used in constructing interpolation
  * `ydata::Vector{Float64}`: y data used in constructing interpolation
  * `x::Float64`: point to evaluate spline at

**Returns**

  * `y::Float64`: value at x using linear interpolation
