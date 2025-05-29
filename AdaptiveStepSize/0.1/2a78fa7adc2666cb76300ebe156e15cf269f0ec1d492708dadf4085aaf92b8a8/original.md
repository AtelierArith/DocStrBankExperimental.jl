```
points_linear_singular(f, domain, singularities::Vector{T}, tol::T; scan_step = (domain[end] - domain[begin]) / 100) where T <: Real
```

Computes points used for a linear interpolation of the function `f` in the given `domain` within a tolerance `tol`. Manages singular points though the array `singularities`.

See [`points_linear`](@ref) for an in depth description of the arguments. This function needs the additional argument `singularities`. This must be a `Vector{T}` where `T<:Real` that contains each singular point.

A singularity in this case is a point at which the function is not well-behaved, like `abs(x)` at x = 0, where the function is continuous but not differentiable.

If the function has several singularities, we can write those in the `singularities` vector. The function `points_linear` will be applied at each subinterval. In addition, the second derivative will never be computed at those endpoints, i.e., at the `singularities` and the `domain` points. Note that `f` **will be** evaluated at the endpoints and it should handle those discontinuities properly. It is the user responsability to do so.

## Notes

If you have a piecewise function, it might be convenient to apply [`points_linear`](@ref) at each interval of the function, instead of passing the `singularities` vector here. The reason is that the result contains just one big pair `xs` and `ys` vectors and it is not aware of the points where piecewise function is not continuous, hence producing undesiderable results in the interpolation.

The safest bet here is linearly interpolate each region of the piecewise function separately.
