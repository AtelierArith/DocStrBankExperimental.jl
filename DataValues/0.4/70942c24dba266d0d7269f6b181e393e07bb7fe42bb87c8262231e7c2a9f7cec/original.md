```
dropna(X::AbstractVector)
```

Return a vector containing only the non-missing entries of `X`, unwrapping `DataValue` entries. A copy is always returned, even when `X` does not contain any missing values.
