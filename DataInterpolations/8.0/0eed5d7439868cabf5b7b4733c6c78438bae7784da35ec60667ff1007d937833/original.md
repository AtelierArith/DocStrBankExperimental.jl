```
function SmoothArcLengthInterpolation(
    u::AbstractMatrix,
    d::AbstractMatrix
    [, make_intersections::Val{<:Bool}];
    shape_itp::Union{AbstractInterpolation, Nothing} = nothing,
    extrapolation::ExtrapolationType.T = ExtrapolationType.None,
    extrapolation_left::ExtrapolationType.T = ExtrapolationType.None,
    extrapolation_right::ExtrapolationType.T = ExtrapolationType.None,
    cache_parameters::Bool = false,
    assume_linear_t = 1e-2,
    in_place::Bool = true)
```

Make a C¹ smooth unit speed interpolation through the given data with the given tangents using line segments and circle segments.

## Arguments

  * `u`: The data to be interpolated in matrix form; (ndim, ndata).
  * `d`: The tangents to the curve in the points `u`.
  * `make_intersections`: Whether additional (point, tangent) pairs have to be added in between the provided data to ensure that the consecutive (tangent) lines intersect. Defaults to `Val(true)`.

## Keyword Arguments

  * `shape_itp`: The interpolation that is being approximated, if one exists. Note that this interpolation is not being used; it is just passed along to keep track of where the shape of the `SmoothArcLengthInterpolation` originated.
  * `extrapolation`: The extrapolation type applied left and right of the data. Possible options are `ExtrapolationType.None` (default), `ExtrapolationType.Constant`, `ExtrapolationType.Linear` `ExtrapolationType.Extension`, `ExtrapolationType.Periodic` and `ExtrapolationType.Reflective`.
  * `extrapolation_left`: The extrapolation type applied left of the data. See `extrapolation` for the possible options. This keyword is ignored if `extrapolation != Extrapolation.none`.
  * `extrapolation_right`: The extrapolation type applied right of the data. See `extrapolation` for the possible options. This keyword is ignored if `extrapolation != Extrapolation.none`.
  * `assume_linear_t`: boolean value to specify a faster index lookup behaviour for evenly-distributed abscissae. Alternatively, a numerical threshold may be specified for a test based on the normalized standard deviation of the difference with respect to the straight line (see [`looks_linear`](@ref)). Defaults to 1e-2.
