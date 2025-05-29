```
interpolate!(I::SplineInterpolation, y::AbstractVector)
```

Update spline interpolation with new data.

This function allows to reuse a [`SplineInterpolation`](@ref) returned by a previous call to [`interpolate`](@ref), using new data on the same locations `x`.

See [`interpolate`](@ref) for details.
