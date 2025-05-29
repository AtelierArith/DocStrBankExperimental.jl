```
nrms(res::AbstractVector{OpticalResidual{T, U}} [,
    fit::LeastSquaresFit{T}]) where {T <: Real, U <: Number}
```

Return the normalized root mean square error of `res`. If `fit` is given, evaluate the residuals in `fit.x`.

See also [`chi2`](@ref) and [`nms`](@ref).
