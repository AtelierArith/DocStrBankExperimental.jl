```
set_precision(x::Type{<:AbstractFloat}=Float64)
```

Set the precision for MicroMagnetic simulations.

This function allows you to specify the precision of floating-point numbers to be used in MicroMagnetic simulations.  By default, it sets the precision to `Float64`. If single-precision computation is required, you can specify `Float32`.

# Example

```julia
set_precision(Float32)
```
