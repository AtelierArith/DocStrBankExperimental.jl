```
smooth(x, y, bandwidth, xeval; leafSize=10, rtol=atol>0 ? 0 : 1e-3, atol=0)
```

Evaluate the Gaussian Kernel Smoother of a set of data points with coordinates `x` and values `y`, with the specified `bandwidth`, at the coordinates in `xeval`. The value of the smoothed function `f` at `x₀` is given by `f(x₀) := ∑ᵢyᵢwᵢ / ∑ᵢwᵢ`, where `wᵢ := exp(-(x₀-xᵢ)²/2bandwidth²)`.

The accuracy of the result is controlled by `rtol` and `atol`. Lower and upper bounds `lb≤f(x₀)≤ub` are gradually improved until `isapprox(lb,ub;rtol=rtol,atol=atol)`.

It is much more efficient to call `smooth` once with vector/matrix arguments for `xeval` and/or `bandwidth` than to call `smooth` multiple times.

# Examples

```julia-repl
julia> smooth([0.0,1.0], [2.0,4.0], 1.0, [0.1, 0.5, 0.9])
3-element Array{Float64,1}:
 2.802624679775096
 3.0
 3.197375320224904
```

See also `GaussianKernelSmoother`, `density`.
