SamplingOp(pattern::Array{Int}, shape::Tuple)

builds a `LinearOperator` which only returns the vector elements at positions indicated by pattern.

# Arguents

  * `pattern::Array{Int}` - indices to sample
  * `shape::Tuple`        - size of the array to sample
