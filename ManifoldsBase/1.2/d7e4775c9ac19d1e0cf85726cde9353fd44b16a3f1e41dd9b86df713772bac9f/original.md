```
default_basis(M::AbstractManifold, ::typeof(p); kwargs...)
default_basis(M::AbstractManifold; kwargs...)
```

Provide a default basis for a manifold's tangent space. This can be specific for different points `p` on `M` The global default for both is the [`DefaultOrthonormalBasis`](@ref) with the same number type as `M`.

This method can also be specified more precisely with a point type `T`, for the case that on a `M` there are two different representations of points, which provide different inverse retraction methods.

## Keyword arguments

  * `field::`[`AbstractNumbers`](@ref) field for the coefficients of the basis
