```
QuantileRegression
```

Quantile regression representation

## Fields

  * `τ`: the quantile value
  * `X`: the model matrix
  * `β`: the coefficients
  * `y`: the response vector
  * `wts`: the weights
  * `wrkres`: the working residuals
  * `formula`: either a `FormulaTerm` object or `nothing`
  * `fitdispersion`: if true, the dispersion is estimated otherwise it is kept fixed
  * `fitted`: if true, the model was already fitted
