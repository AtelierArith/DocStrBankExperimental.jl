```
@reshape long y1 y2 ... i(varlist) j(var) 
@reshape wide y1 y2 ... i(varlist) j(var)
```

Reshape the data frame from wide to long or from long to wide format. The variables `y1`, `y2`, etc. are the variables to be reshaped. The `i(var)` and `j(var)` are the variables that define the row and column indices in the reshaped data frame.

The option `i()` may include multiple variables, like `i(var1, var2, var3)`. The option `j()` must include only one variable.
