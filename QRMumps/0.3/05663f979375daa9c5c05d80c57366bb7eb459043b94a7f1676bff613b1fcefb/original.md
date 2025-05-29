```
qrm_spmat_mv!(spmat, alpha, x, beta, y; transp='n')
```

This subroutine performs a matrix-vector product of the type `y = αAx + βy`, `y = αAᵀx + βy` or `y = αAᴴx + βy`.

#### Input Arguments :

  * `spmat`: the input matrix.
  * `alpha`, `beta` : the α and β scalars
  * `x`: the x vector(s).
  * `y`: the y vector(s).
  * `transp`: whether to multiply by A, Aᵀ or Aᴴ. Can be either `'t'`, `'c'` or `'n'`.
