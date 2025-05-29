```
computecalibration(preds::AbstractVector{<:Normal}, truevals::AbstractVector{<:Real}; pvals)
computecalibration(preds::AbstractVector{<:MvNormal}, truevals::AbstractVector{<:AbstractVector{<:Real}}; pvals)
```

Compute calibration for a series of predicted (uni- or multivariate) normal distributions given a series of true observations using central prediction sets.

Returns a named tuple `(; pvals, calibrationvals)`. If the predictions are well calibrated, then `pvals ≈ calibrationvals` for all indices. Plotting `plot(pvals, calibrationvals)` should then give a straight line from (0, 0), to (1, 1).

# kwargs

  * `pvals`: The probabilities to evaluate the coverage at. Defaults to `0:0.05:1`.
