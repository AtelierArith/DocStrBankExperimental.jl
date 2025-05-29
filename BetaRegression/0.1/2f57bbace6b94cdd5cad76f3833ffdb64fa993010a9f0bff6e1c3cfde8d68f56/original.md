```
params(model::BetaRegressionModel)
```

Return the vector of estimated model parameters $\theta = [\beta_1, \ldots, \beta_p, \phi]$, i.e. the regression coefficients and precision.

!!! danger
    Mutating this array may invalidate the model object.


See also: [`coef`](@ref), [`precision`](@ref)
