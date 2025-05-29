`interpolate(knots::Vector{T}, values::Vector{T},              d1_knots::Vector{T}, d1_values::Vector{T},              d2_knots::Vector{T}, d2_values::Vector{T},              kernel :: RK, factorize = true) where {T <: AbstractFloat, RK <: ReproducingKernel_3}`

Create an interpolating normal spline by values of function and it's first and second derivatives in knots.

# Arguments

  * `knots::Vector{T}`: locations of given function values.
  * `values::Vector{T}`: function values in `knots`.
  * `d1_knots::Vector{T}`: locations of given function derivative values.
  * `d1_values::Vector{T}`: values of function derivative in `d1_knots`.
  * `d2_knots::Vector{T}`: locations of given function second derivative values.
  * `d2_values::Vector{T}`: values of function second derivative in `d2_knots`.
  * `kernel::RK`: reproducing kernel of Hilbert space the normal spline is constructed in.               It must be a struct object of the following type:                 `RK_W3` or `RK_H3` - the spline is constructing as a twice differentiable function.
  * `factorize::Bool`: defines if it is necessary to compute the Gram matrix factorization.                 Must be set to `true` if the spline is constructing first time.                 Can be set to `false` if the spline is constructing with the same knots                 as it was done first time but with different function values in knots.

Returns : nothing.
