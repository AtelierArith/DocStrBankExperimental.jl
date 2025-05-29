```
kronrod([T,] n)
kronrod([T,] n, a, b)
```

Compute $2n+1$ Kronrod points `x[i]` and weights `w[i]` based on the description in Laurie (1997), appendix A, for integrating on the interval $(a,b)$ (defaulting to $[-1,1]$).

If `a` and `b` are not passed, since the rule is symmetric, this only returns the `n+1` points with `x <= 0`. The function Also computes the embedded `n`-point Gauss quadrature weights `wg` (again for `x <= 0` if `a` and `b` are not passed), corresponding to the points `x[2:2:end]`. Returns `(x,w,wg)` in O(`n`²) operations.

`T` is an optional parameter specifying the floating-point type, defaulting to `Float64`. Arbitrary precision (`BigFloat`) is also supported.

Given these points and weights, the estimated integral `I` and error `E` can be computed for an integrand `f(x)` as follows:

```julia
x, w, wg = kronrod(n)
fx⁰ = f(x[end])                # f(0)
x⁻ = x[1:end-1]                # the x < 0 Kronrod points
fx = f.(x⁻) .+ f.((-).(x⁻))    # f(x < 0) + f(x > 0)
I = sum(fx .* w[1:end-1]) + fx⁰ * w[end]
if isodd(n)
    E = abs(sum(fx[2:2:end] .* wg[1:end-1]) + fx⁰*wg[end] - I)
else
    E = abs(sum(fx[2:2:end] .* wg[1:end])- I)
end
```
