```
isapprox(M::AbstractLieGroup, g, h; kwargs...)
```

Check if points `g` and `h` from [`AbstractLieGroup`](@ref) are approximately equal. this function calls the corresponding [`isapprox`](@extref `Base.isapprox-Tuple{AbstractManifold, Any, Any, Any}`) on the [`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`) after handling the cases where one or more of the points are the [`Identity`](@ref). All keyword argments are passed to this function as well.
