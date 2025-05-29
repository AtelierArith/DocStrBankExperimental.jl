```
has_storage(a::AbstractStateAction, ::VectorStorageKey{key}) where {key}
```

Return whether the [`AbstractStateAction`](@ref) `a` has a point value stored at the `Symbol` `key`.
