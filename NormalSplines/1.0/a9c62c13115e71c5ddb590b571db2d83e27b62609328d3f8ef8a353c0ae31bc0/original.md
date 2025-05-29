`evaluate(point::T, derivative::Int = 0) where T <: AbstractFloat`

Evaluate normal spline and it's derivatives.

# Arguments

  * `point::T`: location at which spline or its derivative are evaluating.
  * `derivative::Int`: `0` - spline evaluation.                    `1` - first derivative of spline evaluation.                    `2` - second derivative of spline evaluation.

Returns: spline value or its derivative at the `point` location.
