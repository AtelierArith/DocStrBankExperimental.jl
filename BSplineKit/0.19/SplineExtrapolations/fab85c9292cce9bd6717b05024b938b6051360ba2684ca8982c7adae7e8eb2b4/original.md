```
extrapolate(S::Union{Spline, SplineWrapper}, method::AbstractExtrapolationMethod)
```

Construct a [`SplineExtrapolation`](@ref) from the given spline `S` (which can also be the result of an interpolation).
