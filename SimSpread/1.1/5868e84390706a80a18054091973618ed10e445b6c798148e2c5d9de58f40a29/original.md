```
meanperformance(confusion::AbstractVector{ROCNums{Int64}}, metric::Function)
```

Get mean performance of a given metric over a set of confusion matrices.

# Arguments

  * `confusion::AbstractVector{ROCNums{Int64}}`: Confusion matrices
  * `̂metric::Function`: Performance metric function to use in evaluation.
