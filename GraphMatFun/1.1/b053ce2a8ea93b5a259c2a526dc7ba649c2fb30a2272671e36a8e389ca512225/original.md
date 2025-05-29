```
adjust_for_errtype!(A, b, objfun_vals, errtype)
```

Adjusts the matrix `A` and vector `b` to `errtype`. `A` is a matrix, e.g., the Jacobian or system matrix in a least squares problem. `b` is a vector, e.g., the residuals or the right-hand side in a lieast squares problem. `objfun_vals` is a vector of objective function values, and `errtype` can be `:abserr` or `:relerr`, i.e., absolute error or relative error.
