```
geometric_interpolation(::AbstractCell)::ScalarInterpolation
geometric_interpolation(::Type{<:AbstractCell})::ScalarInterpolation
```

Each `AbstractCell` type has a unique geometric interpolation describing its geometry. This function returns that interpolation, which is always a scalar interpolation.
