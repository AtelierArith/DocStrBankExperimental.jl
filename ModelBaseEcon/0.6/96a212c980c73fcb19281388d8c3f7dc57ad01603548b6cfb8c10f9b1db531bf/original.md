```
export_sstate!(container, model)
```

Fill the given container with the steady state solution stored in the  given model. The value for each variable will be a number, if the variable has zero slope, or else a named tuple of the form `(level = NUM, slope=NUM)`.
