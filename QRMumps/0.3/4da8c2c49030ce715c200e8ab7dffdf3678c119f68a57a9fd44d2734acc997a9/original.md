```
qrm_spposv!(spmat, b, x)
```

This function can be used to solve a linear symmetric, positive definite problem. It is a shortcut for the sequence

```
x = b
qrm_analyse!(spmat, spfct; transp='n')
qrm_factorize!(spmat, spfct; transp='n')
qrm_solve!(spfct, x, x; transp='t')
qrm_solve!(spfct, x, x; transp='t')
```

#### Input Arguments :

  * `spmat`: the input matrix.
  * `b`: the right-hand side(s).
  * `x`: the solution vector(s).
