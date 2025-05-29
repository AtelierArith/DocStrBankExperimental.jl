```
struct RQSpline{T<:Real,N,...} <: Function
```

Represents a rational quadratic spline function or a set of such functions for multiple dimensions and samples.

Implements the splines originally proposed by Gregory and Delbourgo  (https://doi.org/10.1093/imanum/2.2.123)

Constructors:

```julia
RQSpline(pX::AbstractVector{<:Real}, pY::AbstractVector{<:Real}, dYdX::AbstractVector{<:Real})
RQSpline(pX::AbstractArray{<:Real,3}, pY::AbstractArray{<:Real,3}, dYdX::AbstractArray{<:Real,3})
```

Fields:

  * `pX`: An array that holds the x-position of the spline knots.
  * `pY`: An array that holds the y-position of the spline knots.
  * `dYdX`: An array that holds the derivative at the spline knots.

`pX`, `pY` and `dYdX` may be

  * vectors of length `K+1`, representing a one-dimensional spline with `K` segments, or
  * three-dimensional arrays of the shape `K+1 x n_dims x n_samples`, representing a set of splines for different dimensions and input samples.

Requirements for the fields: 

Each spline is continued with the identity function beyond its first and last knot. So to ensure the continuity and differentiability of the splines, the first and last knots must lie on the  diagonal through 0, and the derivatives at these knots must be 1. Formally:  For parameter vectors `pX[1] == pY[1]` and `pX[end] == pY[end]` and `dYdX[1] == dYdX[end] == 1` must hold. For 3 dimensional parameter arrays `pX[1,:,:] == pY[1,:,:]` and `pX[end,:,:] == pY[end,:,:]` and  `dYdX[1,:,:] .== dYdX[end,:,:] .== 1` must be true.

`RQSpline` supports the InverseFunctions, ChangesOfVariables, and Functors APIs.

Example:

```
using MonotonicSplines

f = RQSpline(posX, posX, dY_dX)
Y = f(X)

using InverseFunctions: inverse
X ≈ inverse(f)(Y)

using ChangesOfVariables: with_logabsdet_jacobian
Y, LADJ = with_logabsdet_jacobian(f, X)
```

When instantiated as a set of multi-dimension/samples splines, `RQSpline` uses the package KernelAbstractions for parallel CPU or GPU processing. Custom `ChainRulesCore` rules are provided for effecient automatic differentation.

Random spline generation is supported and RQSpline comes with specialized support for Plots:

```julia
using MonotonicSplines, Plots, InverseFunctions
f = rand(RQSpline)
plot(f); plot!(inverse(f))
plot(f, xlims = (-6, 6)); plot!(inverse(f), xlims = (-6, 6))
```
