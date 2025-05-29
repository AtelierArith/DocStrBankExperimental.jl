```
BEDROC(y::AbstractVector{Bool}, yhat::AbstractVector; rev::Bool=true, α::AbstractFloat=20.0)
```

The Boltzmann Enhanced Descrimination of the Receiver Operator Characteristic (BEDROC) score is a modification of the Receiver Operator Characteristic (ROC) score that allows for a factor of *early recognition*.

Score takes a value in interval [0, 1] indicating degree to which the predictive model employed detects (early) the positive class.

# Arguments

  * `y::AbstractArray`: Binary class labels. 1 for positive class, 0 otherwise.
  * `̂yhat::AbstractArray`: Prediction scores.
  * `rev::Bool`: True if high values of $yhat$ correlates to positive class (default = true).
  * `α::AbstractFloat`: Early recognition parameter (default = 20.0).

# References

1. Truchon, J.-F., & Bayly, C. I. (2007). Evaluating Virtual Screening Methods:  Good and

Bad Metrics for the “Early Recognition” Problem. Journal of Chemical Information and Modeling, 47(2), 488–508. https://doi.org/10.1021/ci600426e
