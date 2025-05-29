```
meanperformance(y::AbstractVector{Bool}, yhat::AbstractVector{Float64}, metric::Function)
```

Get mean performance of a given metric over a pair of label-prediction vectors.

# Arguments

  * `y::AbstractVector`: Binary class labels. 1 for positive class, 0 otherwise.
  * `̂yhat::AbstractVector`: Prediction score.
  * `̂metric::Function`: Performance metric function to use in evaluation.
