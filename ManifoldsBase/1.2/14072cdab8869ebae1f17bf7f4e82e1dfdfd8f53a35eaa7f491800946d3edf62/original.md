```
X = get_vector(M::AbstractManifold, p, c, B::AbstractBasis=default_basis(M, typeof(p)))
```

Convert a one-dimensional vector of coefficients in a basis `B` of the tangent space at `p` on manifold `M` to a tangent vector `X` at `p`.

Depending on the basis, `p` may not directly represent a point on the manifold. For example if a basis transported along a curve is used, `p` may be the coordinate along the curve.

For the [`CachedBasis`](@ref) keep in mind that the reconstruction from [`get_coordinates`](@ref) requires either a dual basis or the cached basis to be selfdual, for example orthonormal

See also: [`get_coordinates`](@ref), [`get_basis`](@ref), [`default_basis`](@ref)
