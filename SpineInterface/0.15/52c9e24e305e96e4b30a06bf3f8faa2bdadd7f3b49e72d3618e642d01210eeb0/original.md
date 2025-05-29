```
indexed_values(value)
```

A Dict mapping indexes to inner values. In case of a scalar - non-indexed - value, the result is Dict(nothing => value). In case of `Map`, each key in the result is a tuple of all the indexes leading to a value.
