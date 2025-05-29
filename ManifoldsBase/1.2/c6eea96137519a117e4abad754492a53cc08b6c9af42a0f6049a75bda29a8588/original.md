```
embed(M::AbstractManifold, p)
```

Embed point `p` from the [`AbstractManifold`](@ref) `M` into the ambient space. This method is only available for manifolds where implicitly an embedding or ambient space is given. Additionally, `embed` includes changing data representation, if applicable, i.e. if the points on `M` are not represented in the same way as points on the embedding, the representation is changed accordingly.

The default is set in such a way that memory is allocated and `embed!(M, q, p)` is called.

See also: [`EmbeddedManifold`](@ref), [`project`](@ref project(M::AbstractManifold,p))
