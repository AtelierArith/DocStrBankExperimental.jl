```
smooth(gks::GaussianKernelSmoother, bandwidth, xeval; rtol=atol>0 ? 0 : 1e-3, atol=0)
```

Evaluate the Gaussian Kernel Smoother for the given `bandwidth` and `xeval`. The value of the smoothed function `f` at `x₀` is given by `f(x₀) := ∑ᵢyᵢwᵢ / ∑ᵢwᵢ`, where `wᵢ := exp(-(x₀-xᵢ)²/2bandwidth²)`.

The accuracy of the result is controlled by `rtol` and `atol`. Lower and upper bounds `lb≤f(x₀)≤ub` are gradually improved until `isapprox(lb,ub;rtol=rtol,atol=atol)`.

# Examples

```julia-repl
julia> g = GaussianKernelSmoother([0.0,1.0],[2.0,4.0]);
julia> smooth.(g, 1, [0.1, 0.5, 0.9])
3-element Array{Float64,1}:
 2.802624679775096
 3.0
 3.197375320224904
```

See also `GaussianKernelSmoother`, `density`.
