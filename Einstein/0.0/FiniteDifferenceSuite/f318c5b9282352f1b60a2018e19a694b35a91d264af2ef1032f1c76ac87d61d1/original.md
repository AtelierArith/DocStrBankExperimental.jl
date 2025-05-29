```
fdm_operator_matrix(op::AbstractFiniteDifferenceOperator{TR}; boundary::Bool=false, transpose::Bool=false) -> BandedMatrix{TR}
```

Create a banded matrix representation of the finite difference operator.

# Arguments

  * `op::AbstractFiniteDifferenceOperator{TR}`: The finite difference operator
  * `boundary::Bool=true`: Whether to include boundary weights
  * `transpose::Bool=false`: Whether to transpose the matrix
