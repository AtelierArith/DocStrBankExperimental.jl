```
expand_ordinal(df, response; response_recoded, var_id, level_var)
```

Construct a dataframe from source `df` that converts an ordinal variable into a series of binary indicators.  These indicators can then be modeled using binomial GEE with the `OrdinalIndependenceCor` working correlation structure.

`response` must be a column name in `df` containing an ordinal variable.  For each threshold `t` in the unique values of this variable an indicator that the value of the variable is `>= t` is created.  The smallest unique value in `response` is omitted.  The recoded variable is called `response_recoded` and a default name is created if no name is provided.  A variable called `var_id` is created that gives a unique integer label for each set of indicators derived from a common observed ordinal value.  The threshold value used to create each binary indicator is placed into the variable named `level_var`.
