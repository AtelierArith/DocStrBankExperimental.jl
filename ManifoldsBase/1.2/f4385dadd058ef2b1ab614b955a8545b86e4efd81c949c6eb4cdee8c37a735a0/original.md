```
×(M, N)
cross(M, N)
cross(M1, M2, M3,...)
```

Return the [`ProductManifold`](@ref) For two `AbstractManifold`s `M` and `N`, where for the case that one of them is a [`ProductManifold`](@ref) itself, the other is either prepended (if `N` is a product) or appenden (if `M`) is. If both are product manifold, they are combined into one product manifold, keeping the order.

For the case that more than one is a product manifold of these is build with the same approach as above
