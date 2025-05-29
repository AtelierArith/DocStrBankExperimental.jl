```
meanstdperformance(confusion::AbstractVector{ROCNums{Real}}, metric::Function)
```

Get mean and standard deviation performance of a given metric over a set of confusion matrices.

# Arguments

  * `confusion::AbstractVector{ROCNums{Real}}`: Confusion matrix object from MLBase
  * `̂metric::Function`: Performance metric function to use in evaluation.
