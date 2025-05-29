```
qrm_min_norm_semi_normal!(spmat, spfct, b, x, Δx, y; transp='n')
```

This function can be used to solve a linear minimum-norm problem

$$
\min \|x\|_2 \quad s.t. \quad Ax = b
$$

in the case where A is square or underdetermined. Contrary to `qrm_min_norm!`, this function allows to solve the problem without storing the Q-factor in the QR factorization of Aᵀ. It is a shortcut for the sequence

```
qrm_set(spfct, "qrm_keeph", 0)
qrm_analyse!(spmat, spfct, transp = 't')
qrm_factorize!(spmat, spfct, transp = 't')
qrm_solve!(spfct, b, Δx, transp = 't')
qrm_solve!(spfct, Δx, y, transp = 'n')
qrm_spmat_mv!(spmat, T(1),  y, T(0), x, transp = 't')
```

Remark that the Q-factor is not used in this sequence but rather A and R. 

#### Input Arguments :

  * `spmat`: the input matrix.
  * `spfct`: a sparse factorization object of type `qrm_spfct`.
  * `b`: the right-hand side(s).
  * `x`: the solution vector(s).
  * `Δx`: an auxiliary vector (or matrix if x and b are matrices) used to compute the solution, the size of this vector (resp. matrix) is the same as x and can be uninitialized when the function is called.
  * `y`: an auxiliary vector (or matrix if x and b are matrices) used to compute the solution, the size of this vector (resp. matrix) is the same as b and can be uninitialized when the function is called.
  * `transp`: whether to use A, Aᵀ or Aᴴ. Can be either `'t'`, `'c'` or `'n'`.
