```
endogenize!(plan, vars, date)
```

Modify the given plan so that the given variables will be endogenous on the given dates. `vars` can be a `Symbol` or a `String` or a `Vector` of such. `date` can be a moment in time (same type as the plan), or a range or an iterable or a container.
