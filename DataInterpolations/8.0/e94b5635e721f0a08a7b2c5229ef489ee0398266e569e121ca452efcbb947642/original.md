```
function SmoothArcLengthInterpolation(
        shape_itp::AbstractInterpolation;
        m::Integer = 2,
        kwargs...)
```

Approximate the `shape_itp` with a C¹ unit speed interpolation using line segments and circle segments.

## Arguments

  * `shape_itp`: The interpolation to be approximated. Note that for the `SmoothArcLengthInterpolation` to be C¹ smooth, the `shape_itp` must be C¹ smooth as well.

## Keyword Arguments

  * `m`: The number of points at which the shape interpolation is evaluated in each interval between time points. The `SmoothArcLengthInterpolation` converges to the shape interpolation (in shape) as m → ∞.
  * `extrapolation`: The extrapolation type applied left and right of the data. Possible options are `ExtrapolationType.None` (default), `ExtrapolationType.Constant`, `ExtrapolationType.Linear` `ExtrapolationType.Extension`, `ExtrapolationType.Periodic` and `ExtrapolationType.Reflective`.
  * `extrapolation_left`: The extrapolation type applied left of the data. See `extrapolation` for the possible options. This keyword is ignored if `extrapolation != Extrapolation.none`.
  * `extrapolation_right`: The extrapolation type applied right of the data. See `extrapolation` for the possible options. This keyword is ignored if `extrapolation != Extrapolation.none`.
  * `assume_linear_t`: boolean value to specify a faster index lookup behaviour for evenly-distributed abscissae. Alternatively, a numerical threshold may be specified for a test based on the normalized standard deviation of the difference with respect to the straight line (see [`looks_linear`](@ref)). Defaults to 1e-2.
