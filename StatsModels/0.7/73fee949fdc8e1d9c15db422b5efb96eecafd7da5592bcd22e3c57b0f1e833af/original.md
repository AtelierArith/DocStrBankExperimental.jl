```
gvif(model::RegressionModel; scale=false)
```

Compute the generalized variance inflation factor (GVIF).

If `scale=true`, then each GVIF is scaled by the degrees of freedom for (number of coefficients associated with) the predictor: $GVIF^(1 / (2*df))$.

Returns a vector of inflation factors computed for each term except for the intercept. In other words, the corresponding coefficients are `termnames(m)[2:end]`.

The [GVIF](https://doi.org/10.2307/2290467) measures the increase in the variance of a (group of) parameter's estimate in a model with multiple parameters relative to the variance of a parameter's estimate in a model containing only that parameter. For continuous, numerical predictors, the GVIF is the same as the VIF, but for categorical predictors, the GVIF provides a single number for the entire group of contrast-coded coefficients associated with a categorical predictor.

See also [`termnames`](@ref), [`vif`](@ref).

!!! warning
    This method will fail if there is (numerically) perfect multicollinearity, i.e. rank deficiency (in the fixed effects). In that case though, the VIF isn't particularly informative anyway.


# References

Fox, J., & Monette, G. (1992). Generalized Collinearity Diagnostics. Journal of the American Statistical Association, 87(417), 178. doi:10.2307/2290467
