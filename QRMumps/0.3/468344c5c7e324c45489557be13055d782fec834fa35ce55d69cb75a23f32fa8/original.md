```
qrm_refine!(spmat, spfct, x, z, Δx, y)
```

Given an approximate solution x of the linear system RᵀRx ≈ z where R is the R-factor of some QR factorization of size (m, n), compute a refined solution.

### Input Arguments :

  * `spmat`: the input matrix.
  * `spfct`: a sparse factorization object of type `qrm_spfct`.
  * `x`: the approximate solution vector or matrix, the size of this vector (resp. matrix) is n (resp. n×k).
  * `z`: the RHS vector or matrix of the linear system, the size of this vector (resp. matrix) is n (resp. n×k).
  * `Δx`: an auxiliary vector (or matrix if x and z are matrices) used to compute the refinement, the size of this vector (resp. matrix) is n (resp. n×k) and can be uninitialized when the function is called.
  * `y`: an auxiliary vector (or matrix if x and z are matrices) used to compute the refinement, the size of this vector (resp. matrix) is m (resp. m×k) and can be uninitialized when the function is called.
