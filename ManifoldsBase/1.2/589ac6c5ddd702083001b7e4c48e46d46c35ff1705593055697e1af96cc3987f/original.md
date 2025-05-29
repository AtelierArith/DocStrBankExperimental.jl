```
AbstractCotangentVector = AbstractFibreVector{CotangentSpaceType}
```

Type for a cotangent vector of a manifold. While a [`AbstractManifold`](@ref) does not necessarily require this type, for example when it is implemented for `Vector`s or `Matrix` type elements, this type can be used for more complicated representations, semantic verification, or even dispatch for different representations of cotangent vectors and their types on a manifold.
