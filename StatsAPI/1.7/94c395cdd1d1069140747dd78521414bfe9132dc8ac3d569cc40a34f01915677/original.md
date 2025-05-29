```
vif(m::RegressionModel)
```

Compute the variance inflation factor (VIF).

The [VIF](https://en.wikipedia.org/wiki/Variance_inflation_factor) measures the increase in the variance of a parameter's estimate in a model with multiple parameters relative to the variance of a parameter's estimate in a model containing only that parameter.

See also [`gvif`](@ref).

!!! warning
    This method will fail if there is (numerically) perfect multicollinearity, i.e. rank deficiency. In that case though, the VIF is not particularly informative anyway.

