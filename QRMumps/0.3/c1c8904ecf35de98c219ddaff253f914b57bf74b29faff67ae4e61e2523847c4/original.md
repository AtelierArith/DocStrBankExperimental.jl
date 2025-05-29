```
qrm_solve!(spfct, b, x; transp='n')
```

This routine solves the triangular system `Rx = b` or `Rᵀx = b`. It can only be executed once the factorization is done.

#### Input Arguments :

  * `spfct`: the sparse factorization object resulting from the qrm_factorize! function.
  * `b`: the right-hand side(s).
  * `x`: the solution vector(s).
  * `transp`: whether to solve for R, Rᵀ or Rᴴ. Can be either `'t'`, `'c'` or `'n'`.
