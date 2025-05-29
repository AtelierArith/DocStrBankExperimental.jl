```
dimensionality(df)
```

Return the dimensionality of a dataframe `df`.

If the dataframe has variables of various dimensionalities `:mixed` is returned.

If the dataframe is empty (no instances) `:empty` is returned. This behavior can be controlled by setting the keyword argument `force`:

  * `:no` (default): return `:mixed` in case of mixed dimensionality
  * `:max`: return the greatest dimensionality
  * `:min`: return the lowest dimensionality
