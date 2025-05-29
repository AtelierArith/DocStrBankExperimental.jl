```
  unwrap_type(W::Type{<:WrappedArray})
```

Fully unwrap a wrapped array type, i.e., returns the `parent_type` until the result is no longer a wrapped array type. This is useful for accessing properties of the innermost array type.
