```
zero_vector!(M::AbstractManifold, X, p)
```

Save to `X` the tangent vector from the tangent space $T_p\mathcal M$ at `p` that represents the zero vector, i.e. such that retracting `X` to the [`AbstractManifold`](@ref) `M` at `p` produces `p`.
