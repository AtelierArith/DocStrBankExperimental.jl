`interpolate(nodes::Matrix{T}, values::Vector{T}, d_nodes::Matrix{T}, es::Matrix{T}, d_values::Vector{T}, kernel::RK = RK_H1()) where {T <: AbstractFloat, RK <: ReproducingKernel_1}`

Prepare and construct the spline.

# Arguments

  * `nodes`: The function value nodes.          This should be an `n×n_1` matrix, where `n` is dimension of the sampled space          and `n_1` is the number of function value nodes.          It means that each column in the matrix defines one node.
  * `values`: function values at `nodes` nodes.
  * `d_nodes`: The function directional derivative nodes.           This should be an `n×n_2` matrix, where `n` is dimension of the sampled space and           `n_2` is the number of function directional derivative nodes.
  * `es`: Directions of the function directional derivatives.      This should be an `n×n_2` matrix, where `n` is dimension of the sampled space and      `n_2` is the number of function directional derivative nodes.      It means that each column in the matrix defines one direction of the function directional derivative.
  * `d_values`: function directional derivative values at `d_nodes` nodes.
  * `kernel`: reproducing kernel of Bessel potential space the normal spline is constructed in.           It must be a struct object of the following type:             `RK_H1` if the spline is constructing as a differentiable function,             `RK_H2` if the spline is constructing as a twice differentiable function.

Return: the completely initialized `NormalSpline` object that can be passed to `evaluate` function.
