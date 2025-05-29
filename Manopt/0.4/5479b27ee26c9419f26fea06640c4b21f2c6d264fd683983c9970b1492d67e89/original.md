```
has_storage(a::AbstractStateAction, ::PointStorageKey{key}) where {key}
```

Return whether the [`AbstractStateAction`](@ref) `a` has a point value stored at the `Symbol` `key`.
