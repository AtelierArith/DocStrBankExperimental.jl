```
LogLinearFormula(df::Int64)
```

Returns GLM formula can be used in `glm` with `FreqTab` data frame. `df`, is abbreviation for degrees of formula, represents degree of polynomial log-linear method. This function works very slowly. If a fixed degree formula will be used repeatedly, define the formula as a variable.
