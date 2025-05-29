```
AdditionProcess(process, added...)
```

A convenience process for adding processes `added` to the `rhs` of the given `process`. `added` can be a single symbolic expression. Otherwise, `added` can be a `Process` or `Equation`, or multitude of them, in which case it is checked that the `lhs_variable` across all added components matches the `process`.
