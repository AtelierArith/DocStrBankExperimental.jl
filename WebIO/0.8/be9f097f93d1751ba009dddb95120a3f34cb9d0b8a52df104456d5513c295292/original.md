```
Async(assets...)
```

A group ("block") of assets that will be imported with no specified order (asynchronously) in the browser. This is useful when dependencies can be imported in any order. The elements of `assets` may either be [`Asset`](@ref)s themselves, any valid constructor for an [`Asset`](@ref), or a [`Sync`](@ref) or [`Async`](@ref).

If the imports need to be imported sequentially, use [`Sync`](@ref) instead.
