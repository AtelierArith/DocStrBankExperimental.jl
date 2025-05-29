```
get_storage(a::AbstractStateAction, ::PointStorageKey{key}) where {key}
```

Return the internal value of the [`AbstractStateAction`](@ref) `a` at the `Symbol` `key` that represents a point.
