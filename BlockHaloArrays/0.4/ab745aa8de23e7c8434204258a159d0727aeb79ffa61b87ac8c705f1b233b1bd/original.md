```
flatten(A::AbstractBlockHaloArray) -> Array
```

Return a flattened version of a BlockHaloArray. This is a copy, since a view of the current block structure isn't possible.
