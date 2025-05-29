`evaluate(points::Vector{T}, derivative::Int = 0) where T <: AbstractFloat`

Evaluate normal spline and it's derivatives.

# Arguments

  * `points::Vector{T}`: locations at which spline or its derivative are evaluating.
  * `derivative::Int`: `0` - spline evaluation.                    `1` - first derivative of spline evaluation.                    `2` - second derivative of spline evaluation.

Returns: `Vector{T}` of spline values or its derivatives at the locations           defined in `points`.
