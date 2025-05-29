```
embed!(M::AbstractManifold, q, p)
```

Embed point `p` from the [`AbstractManifold`](@ref) `M` into an ambient space. This method is only available for manifolds where implicitly an embedding or ambient space is given. Not implementing this function means, there is no proper embedding for your manifold. Additionally, `embed` might include changing data representation, if applicable, i.e. if points on `M` are not represented in the same way as their counterparts in the embedding, the representation is changed accordingly.

The default is set in such a way that it assumes that the points on `M` are represented in their embedding (for example like the unit vectors in a space to represent the sphere) and hence embedding in the identity by default.

If you have more than one embedding, see [`EmbeddedManifold`](@ref) for defining a second embedding. If your point `p` is already represented in some embedding, see [`AbstractDecoratorManifold`](@ref) how you can avoid reimplementing code from the embedded manifold

See also: [`EmbeddedManifold`](@ref), [`project!`](@ref project!(M::AbstractManifold, q, p))
