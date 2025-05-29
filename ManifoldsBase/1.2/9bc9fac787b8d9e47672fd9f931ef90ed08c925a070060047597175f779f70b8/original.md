```
get_basis(M::AbstractManifold, p, B::AbstractBasis; kwargs...) -> CachedBasis
```

Compute the basis vectors of the tangent space at a point on manifold `M` represented by `p`.

Returned object derives from [`AbstractBasis`](@ref) and may have a field `.vectors` that stores tangent vectors or it may store them implicitly, in which case the function [`get_vectors`](@ref) needs to be used to retrieve the basis vectors.

See also: [`get_coordinates`](@ref), [`get_vector`](@ref)
