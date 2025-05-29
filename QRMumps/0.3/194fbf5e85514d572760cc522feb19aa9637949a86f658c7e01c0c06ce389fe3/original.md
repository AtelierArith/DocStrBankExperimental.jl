```
qrm_residual_norm!(spmat, b, x, nrm; transp='n')
```

This function computes the scaled norm of the residual $\frac{\|b - Ax\|_{\infty}}{\|b\|_{\infty} + \|x\|_{\infty} \|A\|_{\infty}}$, i.e., the normwise backward error.

#### Input Arguments :

  * `spmat`: the input matrix.
  * `b`: the right-hand side(s).
  * `x`: the solution vector(s).
  * `nrm`: the computed norm(s).
  * `transp`: whether to use A, Aᵀ or Aᴴ. Can be either `'t'`, `'c'` or `'n'`.
