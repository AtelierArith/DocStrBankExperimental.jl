```
embed(M::AbstractManifold, p, X)
```

Embed a tangent vector `X` at a point `p` on the [`AbstractManifold`](@ref) `M` into an ambient space. This method is only available for manifolds where implicitly an embedding or ambient space is given. Not implementing this function means, there is no proper embedding for your tangent space(s).

Additionally, `embed` might include changing data representation, if applicable, i.e. if tangent vectors on `M` are not represented in the same way as their counterparts in the embedding, the representation is changed accordingly.

The default is set in such a way that memory is allocated and `embed!(M, Y, p. X)` is called.

If you have more than one embedding, see [`EmbeddedManifold`](@ref) for defining a second embedding. If your tangent vector `X` is already represented in some embedding, see [`AbstractDecoratorManifold`](@ref) how you can avoid reimplementing code from the embedded manifold

See also: [`EmbeddedManifold`](@ref), [`project`](@ref project(M::AbstractManifold, p, X))
