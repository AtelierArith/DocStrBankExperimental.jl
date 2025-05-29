`estimate_epsilon(nodes::Matrix{T}, kernel::RK = RK_H0()) where {T <: AbstractFloat, RK <: ReproducingKernel_0}`

Get the estimation of the 'scaling parameter' of Bessel Potential space the spline being built in. It coincides with the result returned by `get_epsilon` function.

# Arguments

  * `nodes`: The function value nodes.          This should be an `n×n_1` matrix, where `n` is dimension of the sampled space          and `n_1` is the number of function value nodes.          It means that each column in the matrix defines one node.
  * `kernel`: reproducing kernel of Bessel potential space the normal spline will be constructed in.          It must be a struct object of the following type:            `RK_H0` if the spline is constructing as a continuous function,            `RK_H1` if the spline is constructing as a differentiable function,            `RK_H2` if the spline is constructing as a twice differentiable function.

Return: estimation of `ε`.
