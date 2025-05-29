```
quantile(fm::BayesianEVA,p::Real)::Real
```

Compute the quantile of level `p` from the fitted Bayesian model `fm`.

If the model is stationary, then a quantile is returned for each MCMC steps.

If the model is non-stationary, a matrix of quantiles is returned, where each row corresponds to a MCMC step and each column to a covariate.
