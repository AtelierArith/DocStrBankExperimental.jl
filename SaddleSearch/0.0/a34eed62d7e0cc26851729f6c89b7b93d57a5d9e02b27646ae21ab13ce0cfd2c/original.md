`StaticString`: the most basic string variant, integrating potential gradient flow with a fixed step-size.

### Parameters:

  * `alpha` : Euler method integration step length

### Shared Parameters

  * `tol` : residual tolerance
  * `maxnit` : maximum number of iterations
  * `precon_scheme` : preconditioner scheme (localPrecon(), globalPrecon())
  * `path_traverse` : how to travserse path to compute energy (serial(), palindrome())
  * `fixed_ends` : true/false for fixing the ends of the path, default is false
  * `verbose` : how much information to print (0: none, 1:end of iteration, 2:each iteration, 3:file log)
