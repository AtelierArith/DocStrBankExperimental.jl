```
gvif(m::RegressionModel; scale=false)
```

Compute the generalized variance inflation factor (GVIF).

If `scale=true`, then each GVIF is scaled by the degrees of freedom for (number of coefficients associated with) the predictor: $GVIF^(1 / (2*df))$.

The [GVIF](https://doi.org/10.2307/2290467) measures the increase in the variance of a (group of) parameter's estimate in a model with multiple parameters relative to the variance of a parameter's estimate in a model containing only that parameter. For continuous, numerical predictors, the GVIF is the same as the VIF, but for categorical predictors, the GVIF provides a single number for the entire group of contrast-coded coefficients associated with a categorical predictor.

See also [`vif`](@ref).

## References

Fox, J., & Monette, G. (1992). Generalized Collinearity Diagnostics. Journal of the American Statistical Association, 87(417), 178. doi:10.2307/2290467
