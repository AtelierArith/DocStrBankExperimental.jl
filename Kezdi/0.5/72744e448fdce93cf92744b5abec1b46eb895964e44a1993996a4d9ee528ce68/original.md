```
@order y1 y2 ... , [desc] [last] [after=var] [before=var] [alphabetical]
```

Reorder the variables `y1`, `y2`, etc. in the data frame. By default, the variables are ordered in the order they are listed. If `desc` is provided, the variables are ordered in descending order. If `last` is provided, the variables are moved to the end of the data frame. If `after` is provided, the variables are moved after the variable `var`. If `before` is provided, the variables are moved before the variable `var`. If `alphabetical` is provided, the variables are ordered alphabetically.
