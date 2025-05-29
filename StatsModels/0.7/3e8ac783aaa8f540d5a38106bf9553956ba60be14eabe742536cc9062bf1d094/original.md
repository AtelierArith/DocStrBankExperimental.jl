```
termnames(model::StatisticalModel)
```

Return the names of terms used in the formula of `model`.

This is a convenience method for `termnames(formula(model))`, which returns a two-tuple of `termnames` applied to the left and right hand sides of the formula.

For `RegressionModel`s with only continuous predictors, this is the same as `(responsename(model), coefnames(model))` and `coefnames(formula(model))`.

For models with categorical predictors, the returned names reflect the variable name and not the coefficients resulting from the choice of contrast coding.

See also [`coefnames`](@ref).
