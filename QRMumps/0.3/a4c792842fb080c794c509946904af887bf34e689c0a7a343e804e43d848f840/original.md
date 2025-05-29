```
qrm_update_shift_spmat!(shifted_spmat, α)
```

Given a `shifted` block matrix of the form `(A  √α)`, update the parameter `α` in the matrix.

### Input Arguments

  * `shifted_spmat`: the input matrix of the qrm*shifted*spmat type. See `qrm_shifted_spmat` for more information.
  * `α ≥ 0`: the regularization parameter (note the square root in the block matrix representation).
