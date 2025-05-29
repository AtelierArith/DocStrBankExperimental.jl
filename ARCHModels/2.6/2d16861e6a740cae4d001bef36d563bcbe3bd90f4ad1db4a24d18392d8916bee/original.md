```
predict(am::UnivariateARCHModel, what=:volatility, horizon=1; level=0.01)
```

Form a `horizon`-step ahead prediction from `am`. `what` controls which object is predicted. The choices are `:volatility` (the default), `:variance`, `:return`, and `:VaR`. The VaR level can be controlled with the keyword argument `level`.

Not all prediction targets / volatility specifications support multi-step predictions.
