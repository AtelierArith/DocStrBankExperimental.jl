`estimate_epsilon(nodes::Vector{T}, d_nodes::Vector{T}, kernel::RK = RK_H1()) where {T <: AbstractFloat, RK <: ReproducingKernel_1}`

Get an the estimation of the 'scaling parameter' of Bessel Potential space the spline being built in. It coincides with the result returned by `get_epsilon` function.

# Arguments

  * `nodes`: The function value nodes.
  * `d_nodes`: The function derivative nodes.
  * `kernel`: reproducing kernel of Bessel potential space the normal spline is constructed in.           It must be a struct object of the following type:             `RK_H1` if the spline is constructing as a differentiable function,             `RK_H2` if the spline is constructing as a twice differentiable function.

Return: estimation of `ε`.
