```
predict(results, h, nChain, Xnew)
```

Function for forecasting Count Data models.

  * `results`: Estimation results
  * `h`: Number of steps to forecast
  * `nChain`: Number of Chains for simulation based forecast (optional)
  * `Xnew`: New values for regressors (only in case of regressors)

# Example

```julia-repl
# 10-step-ahead forecast
predict(results, 10, 10000)
```

The function either returns point forecasts if `nChain` is not specified or generates multiple time series according to estiamtion results. The latter is used to compute forecast intervals and is the default for INARMA models.
