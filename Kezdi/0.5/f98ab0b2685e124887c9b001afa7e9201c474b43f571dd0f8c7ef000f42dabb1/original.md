```
@regress y x1 x2 ... [@if condition], [robust] [cluster(var1, var2, ...)]
```

Estimate a regression model in `df` with dependent variable `y` and independent variables `x1`, `x2`, etc. If `condition` is provided, the operation is executed only on rows for which the condition is true. If `robust` is provided, robust standard errors are calculated. If `cluster` is provided, clustered standard errors are calculated.

The regression is limited to rows for which all variables are values. Missing values, infinity, and NaN are automatically excluded.
