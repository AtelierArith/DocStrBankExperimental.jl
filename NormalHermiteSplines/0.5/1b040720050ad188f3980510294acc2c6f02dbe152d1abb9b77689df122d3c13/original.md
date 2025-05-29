`evaluate_derivative(spline::NormalSpline{T, RK}, point::T) where {T <: AbstractFloat, RK <: ReproducingKernel_0}`

Evaluate the 1D spline derivative at the `point` location.

# Arguments

  * `spline`: the `NormalSpline` object returned by `interpolate` or `construct` function.
  * `point`: location at which spline derivative is evaluating.

Note: Derivative of spline built with reproducing kernel RK_H0 does not exist at the spline nodes.

Return: the spline derivative value at the `point` location.
