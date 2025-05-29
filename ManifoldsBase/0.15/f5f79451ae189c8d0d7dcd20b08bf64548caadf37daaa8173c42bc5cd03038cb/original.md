```
submanifold_component(M::AbstractManifold, p, i::Integer)
submanifold_component(M::AbstractManifold, p, ::Val{i}) where {i}
submanifold_component(p, i::Integer)
submanifold_component(p, ::Val{i}) where {i}
```

Project the product array `p` on `M` to its `i`th component. A new array is returned.
