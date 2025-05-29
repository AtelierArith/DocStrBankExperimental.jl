```
AbstractManifold{𝔽}
```

A type to represent a (Riemannian) manifold. The [`AbstractManifold`](@ref) is a central type of this interface. It allows to distinguish different implementations of functions like the [`exp`](@ref)onential and [`log`](@ref)arithmic map for different manifolds. Usually, the manifold is the first parameter in any of these functions within `ManifoldsBase.jl`. Based on these, say “elementary” functions, as the two mentioned above, more general functions are built, for example the [`shortest_geodesic`](@ref) and the [`geodesic`](@ref). These should only be overwritten (reimplemented) if for a certain manifold specific, more efficient implementations are possible, that do not just call the elementary functions.

The [`AbstractManifold`] is parametrized by [`AbstractNumbers`](@ref) to distinguish for example real (ℝ) and complex (ℂ) manifolds.

For subtypes the preferred order of parameters is: size and simple value parameters, followed by the [`AbstractNumbers`](@ref) `field`, followed by data type parameters, which might depend on the abstract number field type.
