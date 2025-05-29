```
export_sstate(model)
```

Return a dictionary containing the steady state solution stored in the given model. The value for each variable will be a number, if the variable has zero slope, or a named tuple `(level = NUM, slope=NUM)`.
