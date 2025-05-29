```
create_linear_interpolation(x::Vector{Date},y::Vector{<:Real})
create_linear_interpolation(x::Union{Vector{D},Vector{<:DatePeriod}},y::Vector{<:Real}) where D<:DatePeriod
create_linear_interpolation(x::Vector{R},y::Vector{<:Real}) where R<:Real
```

Makes a piecewise linear interpolation function. This is continuous.

### Inputs

  * `x` - A `Vector` with the x coordinates
  * `y` - A `Vector` with the y coordinates

### Returns

  * A `Piecewise_Function` containing the interpolation function.
