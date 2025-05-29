```
qrm_least_squares!(spmat, b, x; transp='n')
```

This function can be used to solve a linear least squares problem

$$
\min \|Ax − b\|_2
$$

in the case where the input matrix is square or overdetermined. It is a shortcut for the sequence

```
qrm_analyse!(spmat, spfct; transp='n')
qrm_factorize!(spmat, spfct; transp='n')
qrm_apply!(spfct, b; transp='t')
qrm_solve!(spfct, b, x; transp='n')
```

#### Input Arguments :

  * `spmat`: the input matrix.
  * `b`: the ight-hand side(s).
  * `x`: the solution vector(s).
  * `transp`: whether to use A, Aᵀ or Aᴴ. Can be either `'t'`, `'c'` or `'n'`.
