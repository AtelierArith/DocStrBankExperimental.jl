`interpolate(knots::Vector{T}, values::Vector{T}, kernel :: RK, factorize = true) where {T <: AbstractFloat, RK <: ReproducingKernel_1}`

Create an interpolating normal spline by values of function in knots.

# Arguments

  * `knots::Vector{T}`: locations of given function values.
  * `values::Vector{T}`: function values in `knots`.
  * `kernel::RK`: reproducing kernel of Hilbert space the normal spline is constructed in.               It must be a struct object of the following type:                 `RK_W1` or `RK_H1` if the spline is constructing as a continuous function,                 `RK_W2` or `RK_H2` if the spline is constructing as a differentiable function,                 `RK_W3` or `RK_H3` if the spline is constructing as a twice differentiable function.
  * `factorize::Bool`: defines if it is necessary to compute the Gram matrix factorization.                 Must be set to `true` if the spline is constructing first time.                 Can be set to `false` if the spline is constructing with the same knots                 as it was done first time but with different function values in knots.

Returns : nothing.
