```
brent(f, a, b; args=(), atol=2e-12, rtol=4*eps(), maxiter=100)
```

1D root finding using Brent's method.  Based off the brentq implementation in scipy.

**Arguments**

  * `f`: scalar function, that optionally takes additional arguments
  * `a`::Float, b::Float`: bracketing interval for a root - sign changes sign between: (f(a) * f(b) < 0)
  * `args::Tuple`: tuple of additional arguments to pass to f
  * `atol::Float`: absolute tolerance (positive) for root
  * `rtol::Float`: relative tolerance for root
  * `maxiter::Int`: maximum number of iterations allowed

**Returns**

  * `xstar::Float`: a root of f
  * `info::Tuple`: A named tuple containing:

      * `iter::Int`: number of iterations
      * 'fcalls::Int`: number of function calls
      * 'flag::String`: a convergence/error message.
