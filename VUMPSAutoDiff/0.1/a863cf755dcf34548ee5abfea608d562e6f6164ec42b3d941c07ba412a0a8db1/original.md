```
gauge_fixing(AL1, AL2)
```

Compute the optimal gauge transformation between two left-canonical MPS tensors by diagonalizing their transfer matrix. Returns the unitary transformation and convergence metric.

# Arguments

  * `AL1`: Reference left-canonical MPS tensor
  * `AL2`: Target MPS tensor to be gauge-fixed (will be transformed to match AL1's gauge)

# Returns

  * `U::AbstractTensorMap`: Unitary transformation matrix satisfying $AL1 ≈ U * AL2 * U'$
  * `conv_meas::Real`: if AL1 and AL2 are equivalent up to a unitary transformation, this should be 0. This is a measure of the deviation between the MPS's represented by AL1 and AL2
