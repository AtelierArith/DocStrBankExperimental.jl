```
rand(M::ProductManifold; parts_kwargs = map(_ -> (;), M.manifolds))
```

Return a random point on [`ProductManifold`](@ref)  `M`. `parts_kwargs` is a tuple of keyword arguments for `rand` on each manifold in `M.manifolds`.
