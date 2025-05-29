```
qrm_shifted_spmat = qrm_shift_spmat(spmat, α = 0)
```

Given a `spmat` structure representing some sparse matrix `A`, return the block matrix `(A  √α)` as a `qrm_shifted_spmat` type. See `qrm_shifted_spmat` for more information. This can be especially useful when `A` is rank deficient, as choosing `α > 0` acts as a regularization.

### Input Arguments

  * `spmat`: the input matrix
  * `α ≥ 0`: the regularization parameter (note the square root in the block matrix representation).
