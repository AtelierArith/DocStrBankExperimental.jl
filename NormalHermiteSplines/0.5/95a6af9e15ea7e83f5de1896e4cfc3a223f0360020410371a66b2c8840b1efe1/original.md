`get_cond(nodes::Matrix{T}, d_nodes::Matrix{T}, es::Matrix{T}, kernel::RK = RK_H1()) where {T <: AbstractFloat, RK <: ReproducingKernel_1}`

Get a value of the Gram matrix spectral condition number. It is obtained by means of the matrix SVD decomposition and requires $O(N^3)$ operations.

# Arguments

  * `nodes`: The function value nodes.          This should be an `n×n_1` matrix, where `n` is dimension of the sampled space and          `n_1` is the number of function value nodes.           It means that each column in the matrix defines one node.
  * `d_nodes`: The function directional derivatives nodes.            This should be an `n×n_2` matrix, where `n` is dimension of the sampled space and            `n_2` is the number of function directional derivative nodes.
  * `es`: Directions of the function directional derivatives.       This should be an `n×n_2` matrix, where `n` is dimension of the sampled space and       `n_2` is the number of function directional derivative nodes.       It means that each column in the matrix defines one direction of the function directional derivative.
  * `kernel`: reproducing kernel of Bessel potential space the normal spline is constructed in.           It must be a struct object of the following type:             `RK_H1` if the spline is constructing as a differentiable function,             `RK_H2` if the spline is constructing as a twice differentiable function.

Return: a value of the Gram matrix spectral condition number.
