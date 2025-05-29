```
iftrue(bool_condition, value)
iftrue(func, bool_condition)
iftrue(bool_condition) do
  # only executed if bool_condition is true
end
```

Helper to create an Option based on some condition. If `bool_condition` is true, the function `func` is called with no arguments, and its result wrapped into `Identity`. If `bool_condition` is false, `Option()` is returned.
