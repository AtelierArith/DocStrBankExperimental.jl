`evaluate(spline::NormalSpline{T, RK}, points::Matrix{T}) where {T <: AbstractFloat, RK <: ReproducingKernel_0}`

Evaluate the spline values at the locations defined in `points`.

# Arguments

  * `spline: the`NormalSpline`object returned by`interpolate`or`construct` function.
  * `points`: locations at which spline values are evaluating.           This should be an `n×m` matrix, where `n` is dimension of the sampled space           and `m` is the number of locations where spline values are evaluating.           It means that each column in the matrix defines one location.

Return: `Vector{T}` of the spline values at the locations defined in `points`.
