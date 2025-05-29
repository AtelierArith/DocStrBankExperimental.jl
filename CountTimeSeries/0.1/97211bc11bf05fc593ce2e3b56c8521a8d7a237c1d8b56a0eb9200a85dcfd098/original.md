```
Model(model, distr, link, pastObs, pastMean, X,
      external, zi)
```

Wrapper function to define count data models. Default setting is an an IID Poisson process without regressors or zero inflation.

Structs have entries:

  * `distr`: "Poisson", "Negative Binomial", or "GPoisson" (Vector for INARMA)
  * `link`: Vector of length two, "Linear" or "Log" (Vector for INARMA)
  * `pastObs`: Lags considered in autoregressive part
  * `pastMean`: Lags considered in MA/past conditional mean part
  * `X`: Matrix of regressors (row-wise)
  * `external`: Indicator(s) if regressors enter externally
  * `zi`: Indicator, zero inflation Y/N

# Examples

```julia-repl
Model(pastObs = 1:2, pastMean = 1) # INGARCH(2, 1)
Model(pastObs = [1, 2], distr = "NegativeBinomial") # NB-INARCH(2)
Model(model = "INARMA", pastMean = 1, zi = true) # Zero inflated INMA(1)
```

For further details, see [Documentation](https://github.com/ManuelStapper/CountTimeSeries.jl/blob/master/CountTimeSeries_documentation.pdf)
