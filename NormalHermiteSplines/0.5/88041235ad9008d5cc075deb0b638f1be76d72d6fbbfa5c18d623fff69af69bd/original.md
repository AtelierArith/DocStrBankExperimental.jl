`evaluate_one(spline::NormalSpline{T, RK}, point::Vector{T}) where {T <: AbstractFloat, RK <: ReproducingKernel_0}`

Evaluate the spline value at the `point` location.

# Arguments

  * `spline`: the `NormalSpline` object returned by `interpolate` or `construct` function.
  * `point`: location at which spline value is evaluating.          This should be a vector of size `n`, where `n` is dimension of the sampled space.

Return: the spline value at the location defined in `point`.
