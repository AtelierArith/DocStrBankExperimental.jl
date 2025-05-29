`evaluate(spline::NormalSpline{T, RK}, points::Vector{T}) where {T <: AbstractFloat, RK <: ReproducingKernel_0}`

Evaluate the spline values/value at the `points` locations.

# Arguments

  * `spline`: the `NormalSpline` object returned by `interpolate` or `construct` function.
  * `points`: locations at which spline values are evaluating.                      This should be a vector of size `m` where `m` is the number of evaluating points.

Return: spline value at the `point` location.
