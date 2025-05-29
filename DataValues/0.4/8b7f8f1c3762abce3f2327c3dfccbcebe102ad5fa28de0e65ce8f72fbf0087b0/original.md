```
dropna!(X::AbstractVector)
```

Remove missing entries of `X` in-place and return a `Vector` view of the unwrapped `DataValue` entries. If no missing values are present, this is a no-op and `X` is returned.
