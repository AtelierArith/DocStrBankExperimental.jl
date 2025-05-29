```
get_coordinates(M::AbstractManifold, p, X, B::AbstractBasis=default_basis(M, typeof(p)))
get_coordinates(M::AbstractManifold, p, X, B::CachedBasis)
```

Compute a one-dimensional vector of coefficients of the tangent vector `X` at point denoted by `p` on manifold `M` in basis `B`.

Depending on the basis, `p` may not directly represent a point on the manifold. For example if a basis transported along a curve is used, `p` may be the coordinate along the curve. If a [`CachedBasis`](@ref) is provided, their stored vectors are used, otherwise the user has to provide a method to compute the coordinates.

For the [`CachedBasis`](@ref) keep in mind that the reconstruction with [`get_vector`](@ref) requires either a dual basis or the cached basis to be selfdual, for example orthonormal

See also: [`get_vector`](@ref), [`get_basis`](@ref)
