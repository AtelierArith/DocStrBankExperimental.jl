```
qrm_residual_orth!(spmat, r, nrm; transp='n')
```

Computes the quantity $\frac{\|A^T r\|_2}{\|r\|_2}$ which can be used to evaluate the quality of the solution of a least squares problem.

#### Input Arguments :

  * `spmat`: the input matrix.
  * `r`: the residual(s).
  * `nrm`: the computed norm(s).
  * `transp`: whether to use A, Aᵀ or Aᴴ. Can be either `'t'`, `'c'` or `'n'`.
