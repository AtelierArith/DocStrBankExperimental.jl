```
simpson(y, x, dx, even)
```

Simpson.jl is a Julia package to integrate y(x) using samples and the composite Simpson's rule.

If x is nothing, spacing of dx is assumed.

If there are an even number of samples, N, then there are an odd number of intervals (N-1), but Simpson's rule requires an even number of intervals. The parameter 'even' controls how this is handled.

The code is based on SciPy v1.7.1: https://github.com/scipy/scipy/blob/v1.7.1/scipy/integrate/_quadrature.py

# Arguments

  * `y::Vector{<:Real}` : the vector to be integrated.
  * `x::Union{Vector{<:Real}, Nothing}=nothing`, optional : the vector at which `y` is sampled.
  * `dx::Real`, optional : spacing of integration points along axis of `x`. Only used when `x` is nothing. Default is 1.0.
  * `even::Symbol[:avg, :first, :last]`, optional   :avg, default : Average two results:

    1. use the first N-2 intervals with a trapezoidal rule on the last interval and
    2. use the last N-2 intervals with a trapezoidal rule on the first interval.

    :first : Use Simpson's rule for the first N-2 intervals with a trapezoidal rule on the last interval.   :last : Use Simpson's rule for the last N-2 intervals with a trapezoidal rule on the first interval.

# Notes

For an odd number of samples that are equally spaced the result is exact if the function is a polynomial of order 3 or less. If the samples are not equally spaced, then the result is exact only if the function is a polynomial of order 2 or less.

# Examples

```
julia> x = 0:9
julia> y = 0:9
julia> simpson(x, y)
40.5

julia> y = x .^ 3
julia> simpson(y, x)
1642.5

julia> simpson(y, x, even=:first)
1644.5

julia> simpson(y, x, even=:last)
1640.5
```
