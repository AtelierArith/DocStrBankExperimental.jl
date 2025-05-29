```
confint(model::BetaRegressionModel; level=0.95)
```

For a model with $p$ regression coefficients, return a $(p + 1) \times 2$ matrix of confidence intervals for the estimated coefficients and precision at the given `level`.
