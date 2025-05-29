maxperformance(confusion::AbstractVector{ROCNums{Real}}, metric::Function)

Get maximum performance of a given metric over a set of confusion matrices.

# Arguments

  * `confusion::AbstractVector{ROCNums{Real}}`: Confusion matrices.
  * `̂metric::Function`: Performance metric function to use in evaluation.
