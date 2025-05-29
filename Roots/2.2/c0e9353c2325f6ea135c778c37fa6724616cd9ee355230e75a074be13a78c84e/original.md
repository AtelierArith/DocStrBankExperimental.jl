```
secant_method(f, xs; [atol=0.0, rtol=8eps(), maxevals=1000])
```

Perform secant method to solve `f(x) = 0.`

The secant method is an iterative method with update step given by `b - fb/m` where `m` is the slope of the secant line between `(a,fa)` and `(b,fb)`.

The initial values can be specified as a pair of 2, as in `(x₀, x₁)` or `[x₀, x₁]`, or as a single value, `x₁` in which case a value of `x₀` is chosen.

The algorithm returns m when `abs(fm) <= max(atol, abs(m) * rtol)`. If this doesn't occur before `maxevals` steps or the algorithm encounters an issue, a value of `NaN` is returned. If too many steps are taken, the current value is checked to see if there is a sign change for neighboring floating point values.

The `Order1` method for `find_zero` also implements the secant method. This one should be slightly faster, as there are fewer setup costs.

Examples:

```julia
Roots.secant_method(sin, (3,4))
Roots.secant_method(x -> x^5 -x - 1, 1.1)
```

!!! note "Specialization"
    This function will specialize on the function `f`, so that the initial call can take more time than a call to the `Order1()` method, though subsequent calls will be much faster.  Using `FunctionWrappers.jl` can ensure that the initial call is also equally as fast as subsequent ones.

