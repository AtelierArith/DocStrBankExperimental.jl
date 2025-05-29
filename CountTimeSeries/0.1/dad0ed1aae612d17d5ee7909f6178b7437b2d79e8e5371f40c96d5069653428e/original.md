```
INARModel
```

Struct to specify an INAR model. It contains information on

  * `distr`: Distributions (vector)
  * `link`: Link functions (vector)
  * `pastObs`: Past observations included
  * `X`: Regressor matrix
  * `external`: Indicator which regressors enter the system externally
  * `zi`: Indicator. Is zero inflation modelled?
