```
default_approximation_method(M::AbstractManifold, f)
default_approximation_method(M::AbtractManifold, f, T)
```

Specify a default estimation method for an [`AbstractManifold`](@ref) and a specific function `f` and optionally as well a type `T` to distinguish different (point or vector) representations on `M`.

By default, all functions `f` call the signature for just a manifold. The exceptional functions are:

  * `retract` and `retract!` which fall back to [`default_retraction_method`](@ref)
  * `inverse_retract` and `inverse_retract!` which fall back to [`default_inverse_retraction_method`](@ref)
  * any of the vector transport mehods fall back to [`default_vector_transport_method`](@ref)
