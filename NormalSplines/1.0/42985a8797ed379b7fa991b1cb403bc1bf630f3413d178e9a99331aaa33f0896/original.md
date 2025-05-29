`interpolate(knots::Vector{T}, values::Vector{T},              d_knots::Vector{T}, d_values::Vector{T},              kernel :: RK, derivative = 1, factorize = true) where {T <: AbstractFloat, RK <: ReproducingKernel_2}`

Create an interpolating normal spline by values of function and it's first or second derivatives in knots.

# Arguments

  * `knots::Vector{T}`: locations of given function values.
  * `values::Vector{T}`: function values in `knots`.
  * `d_knots::Vector{T}`: locations of given function first derivative values (if `derivative`=`1`)                       or second derivative values (if `derivative`=`2`).
  * `d_values::Vector{T}`: values of function first derivative (if derivative=`1`) or                        values of function second derivative (if derivative=`2`) in `d_knots`.
  * `kernel::RK`: reproducing kernel of Hilbert space the normal spline is constructed in.               In a case when `derivative`=`1`, `kernel` must be a struct object of the following type:                    `RK_W2` or `RK_H2` if the spline is constructing as a differentiable function,                    `RK_W3` or `RK_H3` if the spline is constructing as a twice differentiable function.               In a case when `derivative`=`2`, `kernel` must be a struct object of the following type:                    `RK_W3` or `RK_H3` - the spline is constructing as a twice differentiable function,
  * `derivative::Int`: `1` - `d_knots` and `d_values` provide data of function first derivative,                    `2` - `d_knots` and `d_values` provide data of function second derivative.
  * `factorize::Bool`: defines if it is necessary to compute the Gram matrix factorization.                    Must be set to `true` if the spline is constructing first time.                    Can be set to `false` if the spline is constructing with the same knots                    as it was done first time but with different function values in knots.

Returns : nothing.
