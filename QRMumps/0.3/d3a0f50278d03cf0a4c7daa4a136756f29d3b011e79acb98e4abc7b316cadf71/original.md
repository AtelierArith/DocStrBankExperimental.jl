```
qrm_min_norm!(spmat, b, x; transp='n')
```

This function can be used to solve a linear minimum norm problem

$$
\min \|x\|_2 \quad s.t. \quad Ax = b
$$

in the case where the input matrix is square or underdetermined. It is a shortcut for the sequence

```
qrm_analyse!(spmat, spfct; transp='t')
qrm_factorize!(spmat, spfct; transp='t')
qrm_solve!(spfct, b, x; transp='t')
qrm_apply!(spfct, x; transp='n')
```

#### Input Arguments :

  * `spmat`: the input matrix.
  * `b`: the right-hand side(s).
  * `x`: the solution vector(s).
  * `transp`: whether to use A, Aᵀ or Aᴴ. Can be either `'t'`, `'c'` or `'n'`.
