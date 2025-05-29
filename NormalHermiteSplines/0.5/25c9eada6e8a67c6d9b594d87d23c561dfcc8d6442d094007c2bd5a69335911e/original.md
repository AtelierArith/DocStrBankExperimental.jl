`estimate_epsilon(nodes::Vector{T}, kernel::RK = RK_H0()) where {T <: AbstractFloat, RK <: ReproducingKernel_0}`

Get an the estimation of the 'scaling parameter' of Bessel Potential space the spline being built in. It coincides with the result returned by `get_epsilon` function.

# Arguments

  * `nodes`: The function value nodes.
  * `kernel`: reproducing kernel of Bessel potential space the normal spline is constructed in.           It must be a struct object of the following type:             `RK_H0` if the spline is constructing as a continuous function,             `RK_H1` if the spline is constructing as a differentiable function,             `RK_H2` if the spline is constructing as a twice differentiable function.

Return: estimation of `ε`.
