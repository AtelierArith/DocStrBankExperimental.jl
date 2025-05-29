```
CubicHermiteSpline(du, u, t; extrapolation::ExtrapolationType.T = ExtrapolationType.None, extrapolation_left::ExtrapolationType.T = ExtrapolationType.None,
    extrapolation_right::ExtrapolationType.T = ExtrapolationType.None, cache_parameters = false)
```

It is a Cubic Hermite interpolation, which is a piece-wise third degree polynomial such that the value and the first derivative are equal to given values in the data points.

## Arguments

  * `du`: the derivative at the data points.
  * `u`: data points.
  * `t`: time points.

## Keyword Arguments

  * `extrapolation`: The extrapolation type applied left and right of the data. Possible options are `ExtrapolationType.None` (default), `ExtrapolationType.Constant`, `ExtrapolationType.Linear` `ExtrapolationType.Extension`, `ExtrapolationType.Periodic` and `ExtrapolationType.Reflective`.
  * `extrapolation_left`: The extrapolation type applied left of the data. See `extrapolation` for the possible options. This keyword is ignored if `extrapolation != Extrapolation.none`.
  * `extrapolation_right`: The extrapolation type applied right of the data. See `extrapolation` for the possible options. This keyword is ignored if `extrapolation != Extrapolation.none`.
  * `cache_parameters`: precompute parameters at initialization for faster interpolation computations. Note: if activated, `u` and `t` should not be modified. Defaults to `false`.
  * `assume_linear_t`: boolean value to specify a faster index lookup behaviour for evenly-distributed abscissae. Alternatively, a numerical threshold may be specified for a test based on the normalized standard deviation of the difference with respect to the straight line (see [`looks_linear`](@ref)). Defaults to 1e-2.
