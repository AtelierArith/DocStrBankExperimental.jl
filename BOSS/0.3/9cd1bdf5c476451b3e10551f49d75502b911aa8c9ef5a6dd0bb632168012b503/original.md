```
Semiparametric(; kwargs...)
```

A semiparametric surrogate model (a combination of a parametric model and Gaussian Process).

The parametric model is used as the mean of the Gaussian Process and all parameters and hyperparameters are estimated simultaneously.

# Keywords

  * `parametric::Parametric`: The parametric model used as the GP mean function.
  * `nonparametric::Nonparametric{Nothing}`: The outer GP model without mean.

Note that the parametric model must be defined without noise priors, and the nonparametric model must be defined without mean function.
