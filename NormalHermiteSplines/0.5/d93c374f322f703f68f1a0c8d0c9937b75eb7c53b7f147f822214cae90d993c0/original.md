`estimate_accuracy(spline::NormalSpline{T, RK}) where {T <: AbstractFloat, RK <: ReproducingKernel_0}`

Assess accuracy of interpolation results by analyzing residuals.

# Arguments

  * `spline`: the `NormalSpline` object returned by `construct` or `interpolate` function.

Return: an estimation of the number of significant digits in the interpolation result.
