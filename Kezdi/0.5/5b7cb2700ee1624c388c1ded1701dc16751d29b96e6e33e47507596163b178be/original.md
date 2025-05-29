```
@mvencode y1 y2 [_all] ... [if condition], [mv(value)]
```

Encode missing values in the variables `y1`, `y2`, etc. in the data frame. If `condition` is provided, the operation is executed only on rows for which the condition is true. If `mv` is provided, the missing values are encoded with the value `value`. By default value is `missing` making no changes on the dataframe. Using `_all` encodes all variables of the DataFrame.
