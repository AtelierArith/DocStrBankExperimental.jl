```
project(M::AbstractManifold, p, X)
```

Project ambient space representation of a vector `X` to a tangent vector at point `p` on the [`AbstractManifold`](@ref) `M`. This method is only available for manifolds where implicitly an embedding or ambient space is given. Additionally, `project` includes changing data representation, if applicable, i.e. if the tangents on `M` are not represented in the same way as points on the embedding, the representation is changed accordingly. This is the case for example for Lie groups, when tangent vectors are represented in the Lie algebra. after projection the change to the Lie algebra is perfomed, too.

See also: [`EmbeddedManifold`](@ref), [`embed`](@ref embed(M::AbstractManifold, p, X))
