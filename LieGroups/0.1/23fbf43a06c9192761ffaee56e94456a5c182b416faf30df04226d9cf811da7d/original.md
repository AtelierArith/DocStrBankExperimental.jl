```
is_point(G::AbstractLieGroup, g; kwargs...)
```

Check whether `g` is a valid point on the Lie Group `G`. This falls back to checking whether `g` is a valid point on the [`base_manifold`](@ref)`G`. unless `g` is an [`Identity`](@ref). Then, it is checked whether it is the identity element corresponding to `G`.
