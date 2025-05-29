```
embed!(M::AbstractManifold, Y, p, X)
```

Embed a tangent vector `X` at a point `p` on the [`AbstractManifold`](@ref) `M` into the ambient space and return the result in `Y`. This method is only available for manifolds where implicitly an embedding or ambient space is given. Additionally, `embed!` includes changing data representation, if applicable, i.e. if the tangents on `M` are not represented in the same way as tangents on the embedding, the representation is changed accordingly. This is the case for example for Lie groups, when tangent vectors are represented in the Lie algebra. The embedded tangents are then in the tangent spaces of the embedded base points.

The default is set in such a way that it assumes that the points on `M` are represented in their embedding (for example like the unit vectors in a space to represent the sphere) and hence embedding also for tangent vectors is the identity by default.

See also: [`EmbeddedManifold`](@ref), [`project!`](@ref project!(M::AbstractManifold, Y, p, X))
