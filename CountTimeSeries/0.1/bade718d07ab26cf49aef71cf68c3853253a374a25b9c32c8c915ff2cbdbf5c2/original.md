```
INMAModel
```

Struct to specify an INMA model. It contains information on

  * `distr`: Distributions (vector)
  * `link`: Link functions (vector)
  * `pastMean`: Past mean included
  * `X`: Regressor matrix
  * `external`: Indicator which regressors enter the system externally
  * `zi`: Indicator. Is zero inflation modelled?
