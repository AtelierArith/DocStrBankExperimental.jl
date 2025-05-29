```
interp1(x::Union{Array{Float64, 1}, PyObject},v::Union{Array{Float64, 1}, PyObject},xq::Union{Array{Float64, 1}, PyObject})
```

returns interpolated values of a 1-D function at specific query points using linear interpolation.  Vector x contains the sample points, and v contains the corresponding values, v(x).  Vector xq contains the coordinates of the query points.

!!! info
    `x` should be sorted in ascending order.


# Example

```julia
x = sort(rand(10))
y = constant(@. x^2 + 1.0)
z = [x[1]; x[2]; rand(5) * (x[end]-x[1]) .+ x[1]; x[end]]
u = interp1(x,y,z)
```
