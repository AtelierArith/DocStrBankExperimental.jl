```
is_identity(G::AbstractDecoratorManifold, q; kwargs)
```

Check whether `q` is the identity on the [`IsGroupManifold`](@ref) `G`, i.e. it is either the [`Identity`](@ref)`{O}` with the corresponding [`AbstractGroupOperation`](@ref) `O`, or (approximately) the correct point representation.
