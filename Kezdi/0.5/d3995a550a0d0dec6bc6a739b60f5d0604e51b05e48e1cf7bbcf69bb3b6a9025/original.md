```
@generate y = expr [@if condition]
```

Create a new variable `y` in `df` by evaluating `expr`. If `condition` is provided, the operation is executed only on rows for which the condition is true. When the condition is false, the variable will be missing. 
