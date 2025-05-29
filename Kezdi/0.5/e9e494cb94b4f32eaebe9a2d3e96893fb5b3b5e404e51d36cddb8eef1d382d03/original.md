```
@replace y = expr [@if condition]
```

Replace the values of `y` in `df` with the result of evaluating `expr`. If `condition` is provided, the operation is executed only on rows for which the condition is true. When the condition is false, the variable will be left unchanged.
