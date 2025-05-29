```
create_constant_interpolation_to_right(x::Vector{Date},y::Vector{<:Real})
create_constant_interpolation_to_right(x::Vector{<:Real},y::Vector{<:Real})
create_constant_interpolation_to_right(x::Union{Vector{D},Vector{<:DatePeriod}},y::Vector{<:Real}) where D<:DatePeriod
```

Makes a piecewise constant interpolation function. values from the left are copied to the right.

### Inputs

  * `x` - A `Vector` with the x coordinates
  * `y` - A `Vector` with the y coordinates

### Returns

  * A `Piecewise_Function` containing the interpolation function.
