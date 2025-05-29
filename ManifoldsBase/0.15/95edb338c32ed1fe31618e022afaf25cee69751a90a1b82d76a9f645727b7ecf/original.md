```
norm(M::AbstractManifold, p, X)
```

Compute the norm of tangent vector `X` at point `p` from a [`AbstractManifold`](@ref) `M`. By default this is computed using [`inner`](@ref).
