`construct(spline::NormalSpline{T, RK}, values::Vector{T}, d_values::Vector{T}) where {T <: AbstractFloat, RK <: ReproducingKernel_1}`

Construct the spline by calculating its coefficients and completely initializing the `NormalSpline` object.

# Arguments

  * `spline`: the partly initialized `NormalSpline` object returned by `prepare` function.
  * `values`: function values at `nodes` nodes.
  * `d_values`: function directional derivative values at `d_nodes` nodes.

Return: the completely initialized `NormalSpline` object that can be passed to `evaluate` function         to interpolate the data to required points.
