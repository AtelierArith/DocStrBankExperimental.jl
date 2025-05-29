```
AuROC(y::AbstractVector{Bool}, yhat::AbstractVector)
```

Area under the Receiver Operator Characteristic curve using the trapezoidal rule.

# Arguments

  * `y::AbstractArray`: Binary class labels. 1 for positive class, 0 otherwise.
  * `̂yhat::AbstractArray`: Prediction scores.
