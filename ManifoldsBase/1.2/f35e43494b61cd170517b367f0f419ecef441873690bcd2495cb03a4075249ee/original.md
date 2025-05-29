```
get_vectors(M::AbstractManifold, p, B::AbstractBasis=get_basis(M, p, DefaultOrthonormalBasis()))
```

Get the basis vectors of basis `B` of the tangent space at point `p`. The function may or may not work if passed a basis other than a [`CachedBasis`](@ref). A `CachedBasis` can be obtained by calling [`get_basis`](@ref).
