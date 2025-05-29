```
injectivity_radius(M::AbstractManifold)
```

Infimum of the injectivity radii `injectivity_radius(M,p)` of all points `p` on the [`AbstractManifold`](@ref).

```
injectivity_radius(M::AbstractManifold, p)
```

Return the distance $d$ such that [`exp(M, p, X)`](@ref exp(::AbstractManifold, ::Any, ::Any)) is injective for all tangent vectors shorter than $d$ (i.e. has an inverse).

```
injectivity_radius(M::AbstractManifold[, x], method::AbstractRetractionMethod)
injectivity_radius(M::AbstractManifold, x, method::AbstractRetractionMethod)
```

Distance $d$ such that [`retract(M, p, X, method)`](@ref retract(::AbstractManifold, ::Any, ::Any, ::AbstractRetractionMethod)) is injective for all tangent vectors shorter than $d$ (i.e. has an inverse) for point `p` if provided or all manifold points otherwise.

In order to dispatch on different retraction methods, please either implement `_injectivity_radius(M[, p], m::T)` for your retraction `R` or specifically `injectivity_radius_exp(M[, p])` for the exponential map. By default the variant with a point `p` assumes that the default (without `p`) can ve called as a lower bound.
