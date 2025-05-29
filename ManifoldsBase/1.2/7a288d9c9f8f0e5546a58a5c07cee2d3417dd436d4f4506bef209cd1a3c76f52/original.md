```
zero_vector(M::AbstractManifold, p)
```

Return the tangent vector from the tangent space $T_p\mathcal M$ at `p` on the [`AbstractManifold`](@ref) `M`, that represents the zero vector, i.e. such that a retraction at `p` produces `p`.
