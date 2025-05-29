WeightingOp(weights::Vector{T}, rep::Int=1) where T

generates a `LinearOperator` which multiplies an input vector index-wise with `weights`

# Arguments

  * `weights::Vector{T}` - weights vector
  * `rep::Int=1`         - number of sub-arrays that need to be multiplied with `weights`
