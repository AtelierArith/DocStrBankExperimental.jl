```
density(x, bandwidth, xeval; leafSize=10, rtol=atol>1e-20 ? 0 : 1e-3, atol=1e-20)
```

Evaluate the density of a Gaussian Kernel Smoother of a set of data points with coordinates `x`, with the specified `bandwidth`, at the coordinates in `xeval`. The value of the density `g` at `x₀` is given by `g(x₀) := C∑ᵢexp(-(x₀-xᵢ)²/2bandwidth²)`, where `C` is a constant ensuring that `g` is a probability density function.

The accuracy of the result is controlled by `rtol` and `atol`. Lower and upper bounds `lb≤f(x₀)≤ub` are gradually improved until `isapprox(lb,ub;rtol=rtol,atol=atol)`.

It is much more efficient to call `density` once with vector/matrix arguments for `xeval` and/or `bandwidth` than to call `density` multiple times.

# Examples

```julia-repl
julia> density([0.0,1.0], 1.0, [0.1, 0.5, 0.9])
3-element Array{Float64,1}:
 1.6619892900511566
 1.764993805169191
 1.6619892900511566
```

See also `smooth`, `GaussianKernelSmoother`.
