```
parameter(β0, α, β, η, ϕ, ω)
```

Structure for Count Data models parameters.

  * `β0`: Intercept parameter
  * `α`: Parameters for autoregression
  * `β`: Parameters for MA part/past means
  * `η`: Regressor parameters
  * `ϕ`: Overdispersion parameter (Negative Binomial or GPoisson)
  * `ω`: Zero inflation probability

For details, see For details, see [Documentation](https://github.com/ManuelStapper/CountTimeSeries.jl/blob/master/CountTimeSeries_documentation.pdf)
