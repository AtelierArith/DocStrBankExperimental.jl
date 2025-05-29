```
RiskAdjustedCUSUM{G} <: AbstractStatistic
```

Risk-adjusted CUSUM monitoring statistic.

# Arguments

  * `Δ::Float64`: Shift in the linear predictor of the logistic regression model to be detected.
  * `model::G`: Logistic regression model used for prediction. Must have a `predict(model, x)` function.
  * `response::Symbol`: Name of the response variable in the `DataFrame`.
  * `value::Float64`: Initial value of the statistic. Defaults to `0.0`.

# References

Steiner, S. H., Cook, R. J., Farewell, V. T., Treasure, T. (2000). Monitoring surgical performance using risk-adjusted cumulative sum charts. Biostatistics, 1(4), 441-452. https://doi.org/10.1093/biostatistics/1.4.441 ```
