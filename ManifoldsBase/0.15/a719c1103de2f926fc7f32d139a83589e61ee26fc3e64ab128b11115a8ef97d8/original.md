```
copyto!(M::AbstractManifold, Y, p, X)
```

Copy the value(s) from `X` to `Y`, where both are tangent vectors from the tangent space at `p` on the [`AbstractManifold`](@ref) `M`. This function defaults to calling `copyto!(Y, X)`, but it might be useful to overwrite the function at the level, where also information from `p` and `M` can be accessed.
