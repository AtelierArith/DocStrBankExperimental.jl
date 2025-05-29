```
autotype(X; kw...)
```

Return a dictionary of suggested scitypes for each column of `X`, a table or an array based on rules

## Kwargs

  * `only_changes=true`:       if true, return only a dictionary of the names for                             which applying autotype differs from just using                             the ambient convention. When coercing with                             autotype, `only_changes` should be true.
  * `rules=(:few_to_finite,)`: the set of rules to apply.
