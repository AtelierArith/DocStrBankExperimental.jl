```
recallatL(y, yhat, L)
```

Get mean recall@L per group as proposed by Wu, et al (2017).

# Arguments

  * `y::AbstractVector`: Binary class labels. 1 for positive class, 0 otherwise.
  * `̂yhat::AbstractVector`: Prediction score.
  * `̂grouping::AbstractVector`: Group labels.
  * `L::Integer`: Length to consider to calculate metrics (default = 20).
