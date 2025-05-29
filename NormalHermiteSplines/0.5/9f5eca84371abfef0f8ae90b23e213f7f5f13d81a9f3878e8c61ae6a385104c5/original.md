`evaluate_gradient(spline::NormalSpline{T, RK}, point::Vector{T}) where {T <: AbstractFloat, RK <: ReproducingKernel_0}`

Evaluate gradient of the spline at the location defined in `point`.

# Arguments

  * `spline`: the `NormalSpline` object returned by `interpolate` or `construct` function.
  * `point`: location at which gradient value is evaluating.          This should be a vector of size `n`, where `n` is dimension of the sampled space.

Note: Gradient of spline built with reproducing kernel RK_H0 does not exist at the spline nodes.

Return: `Vector{T}` - gradient of the spline at the location defined in `point`.
