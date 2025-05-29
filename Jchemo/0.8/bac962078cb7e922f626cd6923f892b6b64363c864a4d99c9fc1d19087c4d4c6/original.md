```
nipalsmiss(X; kwargs...)
nipalsmiss(X, UUt, VVt; kwargs...)
```

Nipals to compute the first score and loading vectors      of a matrix with missing data.

  * `X` : X-data (n, p).
  * `UUt` : Matrix (n, n) for Gram-Schmidt orthogonalization.
  * `VVt` : Matrix (p, p) for Gram-Schmidt orthogonalization.

Keyword arguments:

  * `tol` : Tolerance value for stopping    the iterations.
  * `maxit` : Maximum nb. of iterations.

See function `nipals`. 

## References

K.R. Gabriel, S. Zamir, Lower rank approximation of  matrices by least squares with any choice of weights,  Technometrics 21 (1979) 489–498.

Wright, K., 2018. Package nipals: Principal Components  Analysis using NIPALS with Gram-Schmidt Orthogonalization.  https://cran.r-project.org/

## Examples

```julia
using Jchemo 

X = [1. 2 missing 4 ; 4 missing 6 7 ; 
    missing 5 6 13 ; missing 18 7 6 ; 
    12 missing 28 7] 

res = nipalsmiss(X)
res.niter
res.sv
res.v
res.u
```
