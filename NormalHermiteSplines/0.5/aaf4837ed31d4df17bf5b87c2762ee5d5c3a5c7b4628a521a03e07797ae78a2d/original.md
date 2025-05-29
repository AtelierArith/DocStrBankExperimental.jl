`interpolate(nodes::Vector{T}, values::Vector{T}, d_nodes::Vector{T}, d_values::Vector{T}, kernel::RK = RK_H1()) where {T <: AbstractFloat, RK <: ReproducingKernel_1}`

Prepare and construct the 1D spline.

# Arguments

  * `nodes`: The function value nodes.
  * `values`: function values at `nodes` nodes.
  * `d_nodes`: The function derivative nodes.
  * `d_values`: function derivative values at `d_nodes` nodes.
  * `kernel`: reproducing kernel of Bessel potential space the normal spline is constructed in.           It must be a struct object of the following type:             `RK_H1` if the spline is constructing as a differentiable function,             `RK_H2` if the spline is constructing as a twice differentiable function.

Return: the completely initialized `NormalSpline` object that can be passed to `evaluate` function.
