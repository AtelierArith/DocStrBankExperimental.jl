```
 SmoothArcLengthInterpolation(
    u::AbstractMatrix{U};
    t::Union{AbstractVector, Nothing} = nothing,
    interpolation_type::Type{<:AbstractInterpolation} = QuadraticSpline,
    kwargs...) where {U}
```

Interpolate in a C¹ smooth way trough the data with unit speed by approximating an interpolation (the shape interpolation) with line segments and circle segments.

## Arguments

  * `u`: The data to be interpolated in matrix form; (ndim, ndata).

NOTE: With this method it is not possible to pass keyword arguments to the constructor of the shape interpolation. If you want to do this, construct the shape interpolation yourself and use the `SmoothArcLengthInterpolation(shape_itp::AbstractInterpolation; kwargs...)` method.

## Keyword Arguments

  * `t`: The time points of the shape interpolation. By default given by the cumulative sum of the Euclidean distances between the points `u`.
  * `interpolation_type`: The type of the shape interpolation. Defaults to `QuadraticSpline`. Note that for the `SmoothArcLengthInterpolation` to be C¹ smooth, the `interpolation_type` must be C¹ smooth as well.
  * `m`: The number of points at which the shape interpolation is evaluated in each interval between time points. The `SmoothArcLengthInterpolation` converges to the shape interpolation (in shape) as m → ∞.
  * `extrapolation`: The extrapolation type applied left and right of the data. Possible options are `ExtrapolationType.None` (default), `ExtrapolationType.Constant`, `ExtrapolationType.Linear` `ExtrapolationType.Extension`, `ExtrapolationType.Periodic` and `ExtrapolationType.Reflective`.
  * `extrapolation_left`: The extrapolation type applied left of the data. See `extrapolation` for the possible options. This keyword is ignored if `extrapolation != Extrapolation.none`.
  * `extrapolation_right`: The extrapolation type applied right of the data. See `extrapolation` for the possible options. This keyword is ignored if `extrapolation != Extrapolation.none`.
  * `assume_linear_t`: boolean value to specify a faster index lookup behaviour for evenly-distributed abscissae. Alternatively, a numerical threshold may be specified for a test based on the normalized standard deviation of the difference with respect to the straight line (see [`looks_linear`](@ref)). Defaults to 1e-2.
