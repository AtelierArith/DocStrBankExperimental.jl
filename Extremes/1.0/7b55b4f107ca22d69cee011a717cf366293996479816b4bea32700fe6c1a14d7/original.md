```
cint(..., confidencelevel::Real=.95)
```

Compute confidence interval or credible interval in the case of Bayesian estimation.

The function can be applied on any [`AbstractFittedExtremeValueModel`](@ref) subtype to obtain a confidence interval on the model parameters. It can also be applied on [`ReturnLevel`](@ref) type to obtain a confidence interval on the return level.

# Implementation

The method used for computing the interval depends on the estimation method. In the case of maximum likelihood estimation, the confidence intervals are computed using the Wald approximation based on the approximate parameter estimates covariance matrix. In the case of Bayesian estimation, the return interval is the highest posterior density estimate based on the MCMC sample. In the case of probability weighted moment estimation, the intervals are computed using a boostrap procedure.
