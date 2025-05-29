```
BDAAutocovMethod <: AbstractAutocovMethod
```

The `BDAAutocovMethod` uses a standard algorithm for estimating the mean autocovariance of MCMC chains.

It is is based on the discussion by [^VehtariGelman2021]. and uses the variogram estimator of the autocorrelation function discussed by [^BDA3].

[^VehtariGelman2021]: Vehtari, A., Gelman, A., Simpson, D., Carpenter, B., & Bürkner, P. C. (2021). Rank-normalization, folding, and localization: An improved $\widehat {R}$ for assessing convergence of MCMC. Bayesian Analysis. doi: [10.1214/20-BA1221](https://doi.org/10.1214/20-BA1221) arXiv: [1903.08008](https://arxiv.org/abs/1903.08008)

[^BDA3]: Gelman, A., Carlin, J. B., Stern, H. S., Dunson, D. B., Vehtari, A., & Rubin, D. B. (2013). Bayesian data analysis. CRC press.
