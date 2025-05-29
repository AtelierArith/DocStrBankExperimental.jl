`evaluate_one(spline::NormalSpline{T, RK}, point::T) where {T <: AbstractFloat, RK <: ReproducingKernel_0}`

Evaluate the 1D spline value at the `point` location.

# Arguments

  * `spline`: the `NormalSpline` object returned by `interpolate` or `construct` function.
  * `point`: location at which spline value is evaluating.

Return: spline value at the `point` location.
