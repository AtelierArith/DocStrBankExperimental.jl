`prepare(nodes::Vector{T}, kernel::RK = RK_H0()) where {T <: AbstractFloat, RK <: ReproducingKernel_0}`

Prepare the 1D spline by constructing and factoring a Gram matrix of the interpolation problem. Initialize the `NormalSpline` object.

# Arguments

  * `nodes`: The function value nodes.
  * `kernel`: reproducing kernel of Bessel potential space the normal spline is constructed in.           It must be a struct object of the following type:             `RK_H0` if the spline is constructing as a continuous function,             `RK_H1` if the spline is constructing as a differentiable function,             `RK_H2` if the spline is constructing as a twice differentiable function.

Return: the partly initialized `NormalSpline` object that must be passed to `construct` function         in order to complete the spline initialization.
