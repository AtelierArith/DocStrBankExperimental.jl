```
SmallCollections.isfasttype(::Type{T}) where T -> Bool
```

Return `true` if elements of type `T` permit fast (for instance, vectorized) operations.

By default, `Base.HWReal`, `Bool`, `Char`, and `Enum` types are considered fast, as well as `Complex`, `Pair`, `Tuple`, `NamedTuple` and `Ref` with fast components.

See `Base.HWReal`.
