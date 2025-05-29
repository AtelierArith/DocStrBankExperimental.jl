```
copyto!(M::AbstractManifold, q, p)
```

Copy the value(s) from `p` to `q`, where both are points on the [`AbstractManifold`](@ref) `M`. This function defaults to calling `copyto!(q, p)`, but it might be useful to overwrite the function at the level, where also information from `M` can be accessed.
