```
containsnan(x)::Bool
```

Checks if `x` definitely is or contains a `NaN` value.

Returns `false` if `containsnan` is not defined for the type of `x` and should also return `false` if checking `x` would be computationally expensive.
