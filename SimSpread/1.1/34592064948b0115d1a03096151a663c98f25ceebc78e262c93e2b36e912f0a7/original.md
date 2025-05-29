```
maxperformance(y::AbstractVector{Bool}, yhat::AbstractVector{Float64}, metric::Function)
```

Get maximum performance of a given metric over a pair of label-prediction vectors.

# Arguments

  * `y::AbstractVector{Bool}`: Binary class labels. 1 for positive class, 0 otherwise.
  * `̂yhat::AbstractVector{Float64}`: Prediction score.
  * `̂metric::Function`: Performance metric function to use in evaluation.
