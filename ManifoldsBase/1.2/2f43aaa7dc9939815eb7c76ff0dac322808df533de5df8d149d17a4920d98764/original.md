```
has_components(M::AbstractManifold)
```

Return whether the [`AbstractManifold`](@ref)`(M)` consists of components, like the [`PowerManifold`](@ref) or the [`ProductManifold`](@ref), that one can iterate over. By default, this function returns `false`.
