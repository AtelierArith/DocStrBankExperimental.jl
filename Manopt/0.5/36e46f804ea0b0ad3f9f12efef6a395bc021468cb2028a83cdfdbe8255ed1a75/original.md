```
get_storage(a::AbstractStateAction, ::VectorStorageKey{key}) where {key}
```

Return the internal value of the [`AbstractStateAction`](@ref) `a` at the `Symbol` `key` that represents a vector.
