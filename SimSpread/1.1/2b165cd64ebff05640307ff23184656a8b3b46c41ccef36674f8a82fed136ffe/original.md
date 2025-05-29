```
precisionatL(y, yhat, L::Integer=20)
```

Get precision@L as proposed by Wu, et al (2017).

# Arguments

  * `y::AbstractVector`: Binary class labels. 1 for positive class, 0 otherwise.
  * `̂yhat::AbstractVector`: Prediction score.
  * `L::Integer`: Length to consider to calculate metrics (default = 20).
