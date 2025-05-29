```
adjr2(model::LinearMixedModel; conditional=false)
adjr²(model::LinearMixedModel; conditional=false)
```

Adjusted coefficient of determination (adjusted R-squared).

For linear models, the adjusted R² is defined as $(1 - (1-R^2)(n-1)/(n-p))$, with $R^2$ the coefficient of determination, $n$ the number of observations, and $p$ the number of coefficients (including the intercept). This definition is generally known as the Wherry Formula I.

For mixed-models, we use this same adjustment for the R² value computed with [`r2`](@ref). `conditional` whether or not the random effects are taken into account when computing the quality of the model fit. They are nonetheless included in the adjustment (i.e. as number $p$ of parameters).

R² is not a clearly defined concept for mixed models, nor does it have all the properties typically expected of the coefficient of determination. See [`r2`](@ref) for more information.
