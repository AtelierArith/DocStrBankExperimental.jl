```
create_constant_interpolation_to_left(x::Vector{Date},y::Vector{<:Real})
create_constant_interpolation_to_left(x::Vector{<:Real},y::Vector{<:Real})
create_constant_interpolation_to_left(x::Union{Vector{D},Vector{<:DatePeriod}},y::Vector{<:Real}) where D<:DatePeriod
```

Makes a piecewise constant interpolation function. values from the right are copied to the left.

### Inputs

  * `x` - A `Vector` with the x coordinates
  * `y` - A `Vector` with the y coordinates

### Returns

  * A `Piecewise_Function` containing the interpolation function.
