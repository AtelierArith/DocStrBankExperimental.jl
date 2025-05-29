```
INARMAResults(y, θ, pars,
  LL, LLs, nPar, nObs, se, CI, Σ,
  model, converged, MLEControl)
```

  * `y`: Time series
  * `θ`: Estimates (vector)
  * `pars`: Estimates (parameter)
  * `λ`: Conditional means
  * `residuals`: Residuals (y - E(y|past)))
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
