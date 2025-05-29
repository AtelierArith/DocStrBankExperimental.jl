```
qrm_least_squares_semi_normal!(spmat, b, x, z, Δx, y; transp='n')
```

This function can be used to solve a linear least squares problem

$$
\min \|Ax − b\|_2
$$

in the case where A is square or overdetermined. Contrary to `qrm_least_squares!`, this function allows to solve the problem without storing the Q-factor of the QR factorization of A.

It is a shortcut for the sequence

```
qrm_set(spfct, "qrm_keeph", 0)
qrm_analyse!(spmat, spfct, transp  = 'n')
qrm_factorize!(spmat, spfct, transp = 'n')
qrm_spmat_mv!(spmat, T(1), b, T(0), z, transp = 't')
qrm_solve!(spfct, z, y, transp = 't')
qrm_solve!(spfct, y, x, transp = 'n')
qrm_refine!(spmat, spfct, x, z, Δx, y)
```

Note that the Q-factor is not used in this sequence; only A and R. 

#### Input Arguments

  * `spmat`: the input matrix.
  * `spfct`: a sparse factorization object of type `qrm_spfct`.
  * `b`: the right-hand side(s).
  * `x`: the solution vector(s).
  * `Δx`: an auxiliary vector (or matrix if b and x are matrices) used to compute the solution, the size of this vector (resp. matrix) is the same as x and can be uninitialized when the function is called.
  * `z`: an auxiliary vector (or matrix if b and x are matrices) used to store the value z = Aᵀb, the size of this vector (resp. matrix) is the same as x and can be uninitialized when the function is called.
  * `y`: an auxiliary vector (or matrix if b and x are matrices) used to compute the solution, the size of this vector (resp. matrix) is the same as b and can be uninitialized when the function is called.
  * `transp`: whether to use A, Aᵀ or Aᴴ. Can be either `'t'`, `'c'` or `'n'`.
