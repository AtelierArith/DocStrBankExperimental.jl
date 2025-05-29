```
INGARCHResults(y, θ, pars, λ, residuals,
      LL, LLs, nPar, nObs, se, CI, Σ,
      model, converged, MLEControl)
```

Structure for estimation results.

  * `y`: Time series
  * `θ`: Estimates (vector)
  * `pars`: Estimates (parameter)
  * `λ`: Conditional means
  * `residuals`: Residuals (y - λ)
  * `LL`: Maximum of likelihood
  * `LLs`: Likelihood contributions
  * `nPar`: Number of parameters
  * `nObs`: Number of observations
  * `se`: Standard errors
  * `CI`: Confidence intervals
  * `Σ`: Covariance matrix of estimator
  * `model`: Model specification
  * `converged`: Indicator, convergence of optimization routine?
  * `MLEControl`: Estimation settings used
