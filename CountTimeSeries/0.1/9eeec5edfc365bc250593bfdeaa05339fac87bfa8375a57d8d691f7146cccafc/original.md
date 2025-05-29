```
INARCHModel
```

Struct to specify an INARCH model. It contains information on

  * `distr`: Distribution
  * `link`: Link function
  * `pastObs`: Past observations included in the conditional mean definition
  * `X`: Regressor matrix
  * `external`: Indicator which regressors enter the system externally
  * `zi`: Indicator. Is zero inflation modelled?
