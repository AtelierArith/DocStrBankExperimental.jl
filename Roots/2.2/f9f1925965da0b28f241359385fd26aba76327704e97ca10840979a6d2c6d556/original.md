```
fzero(f, x0; order=0; kwargs...)
fzero(f, x0, M; kwargs...)
fzero(f, x0, M, N; kwargs...)
fzero(f, x0; kwargs...)
fzero(f, a::Number, b::Number; kwargs...)
fzero(f, a::Number, b::Number; order=?, kwargs...)
fzero(f, fp, a::Number; kwargs...)
```

Find zero of a function using one of several iterative algorithms.

  * `f`: a scalar function or callable object
  * `x0`: an initial guess, a scalar value or tuple of two values
  * `order`: An integer, symbol, or string indicating the algorithm to  use for `find_zero`. The `Order0` default may be specified directly  by `order=0`, `order=:0`, or `order="0"`; `Order1()` by `order=1`,  `order=:1`, `order="1"`, or `order=:secant`; `Order1B()` by  `order="1B"`, etc.
  * `M`: a specific method, as would be passed to `find_zero`, bypassing the use of the `order` keyword
  * `N`: a specific bracketing method. When given, if a bracket is identified, method `N` will be used to finish instead of method `M`.
  * `a`, `b`: When two values are passed along, if no `order` value is specified, `Bisection` will be used over the bracketing interval `(a,b)`. If an `order` value is specified, the value of `x0` will be set to `(a,b)` and the specified method will be used.
  * `fp`: when `fp` is specified (assumed to compute the derivative of `f`), Newton's method will be used
  * `kwargs...`: See `find_zero` for the specification of tolerances and other keyword arguments

Examples:

```
fzero(sin, 3)                  # use Order0() method, the default
fzero(sin, 3, order=:secant)   # use secant method (also just `order=1`)
fzero(sin, 3, Roots.Order1B()) # use secant method variant for multiple roots.
fzero(sin, 3, 4)               # use bisection method over (3,4)
fzero(sin, 3, 4, xatol=1e-6)   # use bisection method until |x_n - x_{n-1}| <= 1e-6
fzero(sin, 3, 3.1, order=1)    # use secant method with x_0=3.0, x_1 = 3.1
fzero(sin, (3, 3.1), order=2)  # use Steffensen's method with x_0=3.0, x_1 = 3.1
fzero(sin, cos, 3)             # use Newton's method
```

!!! note
    Unlike `find_zero`, `fzero` does not specialize on the type of the function argument. This has the advantage of making the first use of the function `f` faster, but subsequent uses slower.

