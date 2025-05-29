`ODEString`: NEB method with adaptive ODE step size selection.

### Parameters:

  * `reltol` : ode solver relative tolerance
  * `threshold` : threshold for error estimate
  * `a0` : initial step, if a0 is not passed then use a default

### NEB only Parameters:

  * `k` : spring constant
  * `interp` : degree of interpolant (1: central differences, >1: splines of degree interp)

### Shared Parameters

  * `tol` : residual tolerance
  * `maxnit` : maximum number of iterations
  * `precon_scheme` : preconditioner scheme (localPrecon(), globalPrecon())
  * `path_traverse` : how to travserse path to compute energy (serial(), palindrome())
  * `fixed_ends` : true/false for fixing the ends of the path, default is false
  * `verbose` : how much information to print (0: none, 1:end of iteration, 2:each iteration, 3:file log)
