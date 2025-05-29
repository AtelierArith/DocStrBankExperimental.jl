`get_epsilon(spline::NormalSpline{T, RK}) where {T <: AbstractFloat, RK <: ReproducingKernel_0}`

Get the 'scaling parameter' of Bessel Potential space the spline was built in.

# Arguments

  * `spline`: the `NormalSpline` object returned by `prepare`, `construct` or `interpolate` function.

Return: `ε` - the 'scaling parameter'.
