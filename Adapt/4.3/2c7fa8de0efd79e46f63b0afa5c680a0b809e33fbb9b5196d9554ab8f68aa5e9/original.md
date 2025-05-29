```
  parent_type(W::Type{<:WrappedArray})
```

Return the parent type of a wrapped array type. This is the type of the array that is wrapped by the wrapper, e.g. `parent_type(SubArray{Int, 1, Matrix{Int}}) == Matrix{Int}`.
