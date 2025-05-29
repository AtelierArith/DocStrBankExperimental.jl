```
iffalse(bool_condition, value)
iffalse(func, bool_condition)
iffalse(bool_condition) do
  # only executed if bool_condition is true
end
```

Helper to create an Option based on some condition. If `bool_condition` is false, the function `func` is called with no arguments, and its result wrapped into `Identity`. If `bool_condition` is true, `Option()` is returned.

Precisely the opposite of [`iftrue`](@ref).
